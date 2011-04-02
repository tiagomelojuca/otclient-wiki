### Identation
* 4 spaces are used for indentation
* Spaces, not tabs!

### Declaring variables
* Variables and functions start with a small letter. Each consecive word in a variable’s
name starts with a capital letter
* Avoid short names and abbreviations whenever possible, use readable names

```C
function myDummyFunction()
{
    int a; // Wrong
    int whorisize; // Wrong
    int hsize; // Wrong
    int windowHSize; // Wrong

    int windowHorizontalSize; // Correct
}
```

* Single character variable names are only okay for counters and temporaries, where the purpose of the variable is obvious
* Classes always start with a big letter.
* Class members variables always begins with m_ fallowed by a lower case

```C
class DummyClass
{
    int mVariable; // Wrong
    int m_Variable; // Wrong
    int m_variable; // Correct
};
```

* Struct member variables must not begin with m_, avoid structs and use only when it feels right
* Global variables begins with g_

### Singletons
* Use the following style to declare singletons
```C
// on game.cpp top
Game g_game;
// on game.h bottom
class Game { };
extern Game g_game;
```

### Iterators
* Use **auto** keyword on every iterator
```C
std::map<int, std::string>::iterator it = myMap.begin(); // Wrong
for(std::map<int, std::string>::iterator it = myMap.begin(); it != myMap.end(); it++) // Wrong
auto it = myMap.begin(); // Correct
for(auto it = myMap.begin(); it != myMap.end(); ++it) // Wrong
```

### Sources files
* Include prerequisites.h first in every header file
* All sources files have the license and copyright note on top

### Documentation
* Comment anything that you feel relevant
* Document functions on headers using /// or /** */ to enable doxygen output