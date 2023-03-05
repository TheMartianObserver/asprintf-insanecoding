# asprintf and vasprintf implementations

## Description

`asprintf()` and `vasprintf()` are C functions which duplicate the
functionality of sprintf() and vsprintf() respectively, except that asprintf()
and vasprintf() allocate a string large enough to hold the output, instead of
requiring to be supplied with a fixed-length buffer as their predecessors do.

[Home](http://asprintf.insanecoding.org/)

## API
### Prototypes:
```c

int asprintf(char **ret, const char *format, ...);
int vasprintf(char **ret, const char *format, va_list ap);
```

Usage:

    ret: A pointer to a char * which will contain the formatted output.
    format: A format string as with printf() and related functions.
    Additional arguments: Any extra arguments are used as with sprintf() and vsprintf().

Return value:

Both functions set *ret to be a pointer to a malloc()'d buffer sufficiently
large to hold the formatted string. This pointer should be passed to free() to
release the allocated storage when it is no longer needed.

The integer value returned by these functions is the number of characters that
were output to the newly allocated string (excluding the final '\0'). To put
it differently, the return value will match that of strlen(*ret).

Upon failure, the returned value will be -1, and *ret will be set to NULL.

Note: Upon failure, other implementations may forget to set *ret and leave it
in an undefined state. Some other implementations may always set *ret upon
failure but forget to assign -1 for the return value in some edge cases.

Examples:

Usage examples are provided with this implementation in the file test.c.
Further resources
Book cover for Understanding and Using C Pointers

If the topics here interest you, but are currently beyond your skills, acquire for yourself a copy of Understanding and Using C Pointers.
This implementation

Rationale and design notes.
Downloads:

    1.0: BZ2 ZIP

Compatible with:

    Linux
    Windows
    GCC (including MinGW)
    Microsoft Visual C++ (MSVC)
    Much more...
