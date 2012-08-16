I am writing this tutorial to help people get started in contributing to otclient by creating new modules and working within otclient lua environment.

**So to start things off I will be covering:**
* the creation of modules.
* go over some of the basics to working within otclients lua environment.
* how to efficiently test your modules and scripts.

**For this tutorial you will need:**
* otclients latest source code from the git repository [otclient repo](https://github.com/edubart/otclient). There is a tutorial on how to work with the git repository [here](http://otclient.info/tutorials/git_workflow.html).
* a text editor of some sort (I like to use [Sublime Text 2](http://www.sublimetext.com/2) or [Notepad++](http://notepad-plus-plus.org/download/v6.1.5.html)) just be sure to read the [code conventions](https://github.com/edubart/otclient/wiki/OTClient-Coding-Style) first too.
* it would also be good to have basic knowledge of lua and programming skills (but this is something you can pick up quickly by practicing).

Now that you have what you need we can get started!

# Creating a New Module
Otclient front end runs off what we call 'modules'. Modules are a way of effectively implementing client features separate to each other. If you are considering creating a new module it is advised that you think about what the feature might be and whether or not it would fit into an already existing module (most likely a game\_xxx module), the modules are found in the /modules directory of otclient.

Their are currently two module 'environments': **Game** and **Client**. Game modules use the prefix game\_ and should be reflecting features that specifically relate back to the player or game environment features for example game\_outfit or game\_mounts are both features that are used in the game environment. Client modules use the prefix client\_ and should be reflecting features that specifically relate back to the client and the client only. It does not have anything to do with the players game environment, e.g. client\_options and client_skins are only directly related to the clients functionality. This might be a little bit hard to visualize for now but you will pick this up more later.

So now that you have an understanding of what a module is and somewhat how they operate we will go ahead and start creating a new one.

## Starting from scratch
We are going to create a fresh module from scratch, the first thing you need to do is create the modules directory. The directory name should reflect the overall feature itself, so we will call ours `game_spells` to start creating a new module that will list all the players spells with their appropriate information. We won't be creating this entire module but we can get started to see how it all works.

* `Create a new directory called game_spells inside the clients /modules directory.`

Inside game\_spells we need to start by adding 3 new base files: spells.lua, spells.otmod and spells.otui for the modules logic, registration, and interface design.

* `Create 3 new base files spells.lua, spells.otmod and spells.otui inside /modules/game_spells`

You might already know what the .lua file represents but what are these new extensions .otmod and .otui?
### .otmod
.otmod file is the file that is used to initialize the module within otclient, it is like a register in that it will register the module for use inside the client. This file generally has a structure like this (I have added comments, if you copy this code be sure to remove the -- comments):
```lua
Module
  name: game_spells -- name of the module (generally the same name as the modules directory.
  description: Display a players spells with their appropriate information -- description of the module explaining what it is.
  author: BeniS -- names of the creators and contributors of the module.
  website: www.otclient.info -- if you have an external website you can link it here.
  sandboxed: true -- Sandboxing is a way of containing the modules variable and functions so that you do not have conflicts between other modules.
  scripts: [ spells.lua ] -- The scripts is the logic behind the module where all the functions are contained.
  @onLoad: init() -- this is where you define the initialization function of the module (we will cover this more later).
  @onUnload: terminate() -- this is where you define the termination function of the module (we will cover this more later)
```

* `Copy the .otmod code above into your spells.otmod file and remove the -- comments.`

### .otui
.otui file is the file that is used to create the modules user interface. This is a custom made styling language specifically designed for otclient called OTML, it feels a lot like CSS formatting for those of you who have experience in webdesign. The typical structure of a .otui file looks like this (this is the start base file, not completed):
```css
MainWindow
  !text: tr('Spells')
  size: 160 450

  @onEnter: modules.game_spells.destroy()
  @onEscape: modules.game_spells.destroy()

  Label
    id: spellsLabel
    !text: tr('Player Spells')
    width: 130
    anchors.top: prev.top
    anchors.left: prev.left
    margin-top: 5
    margin-left: 5
```

**MainWindow** This is the window we will be using for the spell list interface, it is a standard window class derived from `/client_skins/default/styles/windows.otui` styling file it extends Window which extends UIWindow. UIWindow is a base class of this initialization, it controls the widgets functionality and behaviors.
* **!text:** This is the text that is displayed in the MainWindow heading section.
* **size:** this is used to set the MainWindows width/height.
* **@onEnter:** configures the MainWindow widgets onEnter callback (function that will be called when you press the enter key).
* **@onEscape:** configures the MainWindow widgets onEscape callback (function that will be called when you press the escape key).

**Label** This is a label widget that is used for displaying text in most cases. It is a derivative of UILabel class.
* **id:** This is the id that this commonent with alias itself with for referencing using funcitions such as widget:getChildById("spellsLabel")
* **!text:** This is the text that will be displayed by the UILabel widget.
* **width:** This is the width size of the Label.
* **anchors.top/bottom/left/right:** Anchors are where the top/bottom/left/right of the Label should be positioned, this is often based on the previous (prev) UI component or the parents anchors.
* **margin-top/bottom/left/right:** Margins are offsets to the anchors, they will allow you to fine-tune the placement of UI components.

This is just the surface of .otui formatting and styling, there is a lot more that can be done but the main idea is that you get a grasp on how to hierarchy the UI components to display correctly, etc. the OTML styling conventions force you to keep the designing of an interface separate to the logic code for example the .lua.

* `Copy the otui code above into your spells.otui file`

Now that we understand what file is used to register the module and what file(s) are used to build the modules UI we can delve into the modules logic code and try understand how it all works together. The file spells.lua is the file that contains the modules logic code. This is where the spells will be populated and the handling of spell selection and spell display will be controlled.

* `Open the file spells.lua and copy in the following base code to get started.`

We will be picking apart this code to help better understand it. I went ahead and started the base code for you, here it is:
```lua
Spells = nil

spellWindow = nil
selectedSpell = nil
spells = {}

function init()
  connect(g_game, { onOpenSpellWindow = create,
                    onGameEnd = destroy })
end

function terminate()
  disconnect(g_game, { onOpenSpellWindow = create,
                       onGameEnd = destroy })
  destroy()
  
  Spells = nil
end

function Spells.create(spellList)
  spells = spellList
  destroy()

  spellWindow = g_ui.displayUI('spells.otui')
end

function Spells.destroy()
  if spellWindow then
    spellWindow:destroy()
    spellWindow = nil
    selectedSpell = nil
    spells = {}
  end
end

function Spells.selectSpell()
  if table.empty(spells) then
    return
  end
  -- TODO
end
```

The main things I want to focus on here are:
* The variables (spellWindow, selectedSpell and spells).
* The functions (storing of functions and discuss what init and terminate are required for).

**The variables**  
Variables within a sandboxed module do not have to be localized with the keyword `local` as they are inside their own module environment. In the module is `sandboxed: false` then you will need to make sure you localize the variable and reset them inside the terminate function (which we will discuss more later).

Inside this spell module we need to have a way of storing the modules window object, we do this by setting the variable `spellWindow` that we have initialized as nil, but that we will setup soon enough. We also need a way of containing what spell the player has selected which means we should store a reference to the spell somehow using the variable `selectedSpell`. Last but not leave and most likely not last! We need to store the list of spells, we do this with the `spells` variable.

**The functions**  
Functions much like variables are contained within sandboxed modules so localization can vary depending on your preferences. If you are not using a `sandboxed: true` module then you will need to make sure you are localizing and storing functions correctly. I personally like to use a table to store my functions within to keep things
