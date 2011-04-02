### Identation
* 4 spaces are used for indentation
* Spaces, not tabs!

### Declaring variables
* Avoid short names whenever possible, use readable names

```C
int a; // Wrong
int whorisize; // Wrong
int hsize; // Wrong
int windowHSize; // Wrong

int windowHorizontalSize; // Correct
```

* Single character variable names are only okay for counters and temporaries, where the purpose of the variable is obvious
* Variables and functions start with a small letter. Each consecive word in a variable’s
name starts with a capital letter
* Avoid abbreviations
* Classes always start with a big letter.

### Singletons
* Use the following style to declare singletons
```C
// on game.cpp top
Game g_game;
// on game.h bottom
extern Game g_game;
```

### Documentation
* Comment anything that you feel relevant
* Document functions on headers using /// or /** */ to enable doxygen output