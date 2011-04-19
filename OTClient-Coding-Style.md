### Identation
* 4 spaces are used for indentation
* Spaces, not tabs!

### Declaring variables
* Variables/functions start with a small letter and each consecive word starts with a capital letter.
* Avoid short names and abbreviations whenever possible. Use readable names.

```cpp
    int a; // Wrong
    int whorisize; // Wrong
    int hsize; // Wrong
    int windowHSize; // Wrong
    int windowHorizontalSize; // Correct
```

* Single character variable names are only okay for counters, where the purpose of the variable is obvious.
* Classes always start with a big letter.
* Class members variables always begins with m_ fallowed by a lower case.

```cpp
    class DummyClass
    {
        int mVariable; // Wrong
        int m_Variable; // Wrong
        int m_variable; // Correct
    };
```

* Struct member variables must not begin with m_, avoid structs and use only when it feels right.
* Global variables begins with g_
* Use bultin int types:

```cpp
    uint32_t var; // Wrong
    uint32 var; // Correct

    unsigned long var; // Wrong
    ulong var; // Correct
```

### Singletons
* Use the following style to declare singletons:

```cpp
    // on game.cpp top
    Game g_game;
    // on game.h bottom
    class Game { ... };
    extern Game g_game;
```

### Loops and iterators
* Use **auto** keyword on every iterator:

```cpp
    std::map<int, std::string>::iterator it = myMap.begin(); // Wrong
    auto it = myMap.begin(); // Correct

    for(std::map<int, std::string>::iterator it = myMap.begin(); it != myMap.end(); it++) // Wrong
    for(auto it = myMap.begin(); it != myMap.end(); ++it) // Correct
```

* Prefer foreach over iterators when performance isn't needed, as it is clean to read:

```cpp
    for(auto it = files.begin(); it != files.end(); ++it) { } // Wrong
    foreach(const std::string& file, files) { } // Corect
```

### Sources files
* Include prerequisites.h first in every file.
* All sources files must have the license and copyright note on top.
* Only include needed headers.
* Whenever is possible declare classes names instead of including it's headers.

```cpp
    // Wrong
    #include "foo.h"
    class Dummy {
        SomeClass *m_foo;
    };

    // Correct
    class Foo;
    class Dummy {
        SomeClass *m_foo;
    };
```

### Classes
* When using **new** keyword place brackets only when needed:

```cpp
    new DummyClass(); // Wrong
    new DummyClass; // Correct
```

* Avoid empty constructors in sources files.
* Declare destructors only when needed.
* Get methods must have **const** keyword.

### Documentation
* Comment anything that you feel relevant.
* Document functions on headers using /// or to enable doxygen output.

### Algorithms
* Use high level classes like Rect, Point, std::string whenever is possible.
* Use high level APIs, for strings boost algorithm and regex is there.
* Make algorithms readable and organized.
* Comment complex ones.

### Pointers and memory
* Avoid to use **delete** keyword or manage memory on you own, always prefer smart pointers.
* Prefer to pass complex functions variables by referece and using **const** keyword.