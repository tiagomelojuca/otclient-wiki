# The Official OTClient Wiki

## Welcome!
If you are looking for information about OTClient, here is the right place. This is the official community maintained repository of information and documentation for users, developers and contributors.

## About OTClient
OTClient is an alternative Tibia client for usage with otserv.
It aims to be complete and flexible, for that it uses LUA
scripting for all game interface functionality and configurations using a new file type known as OTML, that was created with the purpose to be easy for typing/reading.
OTClient works with a modular system, each functionality is a separated module,
this gives the possibility to users modify anything easily. It also allows to
extend game functionalitty with modules known as "addons", feature inspirited by "World of Warcraft", where
users can create their own game interfaces and functionality on top of the original game. The game interface look and style is completely flexible, you can change styles using a syntax near CSS and QML.

## Getting Started
Getting started with OTClient is simple! OTClient has multi client/protocol support which means it can run different Tibia protocols/clients (from 7.6 to 10.35). In order to run the different versions all you need to do is this:
* Copy the Tibia.dat and Tibia.spr from your regular Tibia client into `/data/things/<version>/` folder.

For example: `/data/things/860/` this will check for the 8.60 tibia dat/spr files here.

Now you can use that client version by selecting it in the login process:

![Version](https://dl.dropbox.com/u/49948294/wiki/getting_started/login.png)

To login to the server you would like to play you can just enter in the **server** and the **port** (like so in the article above)

### Menu
There are menu buttons for the client management and game features located at the top of the client window.

![Client Options](https://dl.dropbox.com/u/49948294/wiki/getting_started/client_options.png)

![Game Options](https://dl.dropbox.com/u/49948294/wiki/getting_started/game_options.png)

For any of the traditional game features, this is where they will be located.

## General Resources
* [[FAQ]]

## Developing Resources
* [[OTClient Coding Style]]
* [[Submitting Patches]]
* [[Compiling on Linux]]
* [[Compiling on Windows]]
* [[Module Tutorial]]
* [[CMake useful options]]