### Before I start, here are some notes:

**Things I will *NOT* teach you:**
* C++
* Lua
* Compiling otclient, there are tutorials over here in the wiki, please check them out.

**Things I will teach you:**
* Basic usage of git.
* Testing your code before pushing.

**Another thing, before diving in, obtain a copy of Git, there are several ways to do this, here are some of them:**
* Compiling from source code (I won't do that)
* Obtaining it by your package manager (Linux or Cygwin)
* The Native way in windows, is obtaining an installer through [here](http://git-scm.com/download/win)

Okay, now you're ready to dive in.
** Step 1**
* Open up Git Shell.
* Obtain a copy of otclient's source code:
```sh
   git clone https://github.com/edubart/otclient.git
```
* Change directory to otclient's source code:
```sh
   cd otclient
```
* Before you do anything, please work on a different branch than master, we will use _tutorial_.
* Tip: to see which branch you're currently working on, do:
```sh
   git branch
```
  Which should (hopefully) output:
  *  master

* Create your work branch, we will be using _tutorial_:
```sh
   git checkout -b tutorial
```
This creates new branch called tutorial and switches to it and is also a shortcut to:
```sh
   git branch tutorial
   git checkout tutorial
```
Make sure you're in the branch tutorial, do:
```sh
   git branch
```
Which should output:
   * master
   * tutorial

Now, the job!
* Step 1, Do some change
![code](http://i.imgur.com/d7q4K.png)

* Step 2, check our changes:
![changes](http://i.imgur.com/N44kp.png)

Like you see, nothing has been added to the repo yet, add it with:
```sh
   git add file
```
Like so:
![add](http://i.imgur.com/WZnuR.png)

* Step 3, make a .patch file
Making a patch file is a simple process, and is done like so:
![patch](http://i.imgur.com/9pCvF.png)

* Step 4, now, send the patch to some developer.
![send_patch](http://i.imgur.com/KIttX.png)

Note, this step is optional (the sending email thing), alternatively you can use github issues to send patches etc. Use whatever you feel comfortable with.
Note, read the manual page for git send-email if you're wondering how this is done.

Job done!
## Bonus
It's good to write the signed-off-by line in your patch, to tell that this is your code, etc.  It has _no use_ but it's still useful to write it, here's a small pic how to:
![signedoffby](http://i.imgur.com/Kpfgh.png)

Happy hacking!