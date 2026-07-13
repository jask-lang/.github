# Introduction

pseudoscript (pssp) is a highly readable scripting language in early development, modeled after pseudo code. The pssp interpreter is fully written in C# without other dependencies. It is just a hobby project for fun and learning, contributions are always welcome!

The main goal is to keep the interpreter itself as small as possible and to implement only those functions internally that are truly necessary or that greatly affects performance.
All other functions should be written directly in pssp to explore and expand the language's capabilities.
A brief summary of the properties of pssp:
* dynamically typed variables (Variables are just a container for any kind of data)
* strongly typed values (pssp enforces strict type checking)
* fully immutable (things in pssp cannot mutate themselves, operations always creating copies)
* data and behaviour are separated (functions are not bound to anything, data is held separated)

Seeing jask for the the first time?
Try the [Getting started guide](TBD)!
For further information, please visit the [Wiki](TBD).
A collection of useful functions written in pssp can be found at [psspstdlib](TBD).

# Examples

## Hello World
```pseudo
set hello to "Hello, World!"
print(hello)
```
pssp aims to be highly readable, easy to maintain, and understandable to beginners. The syntax largely avoids complex notation and is modeled after natural language.

## Functions, conditions, lists, loops and structs...
A more complex example for a direct deep-dive:
```pseudo
struct Edible
    set name to ""
    set number to 0
    set healthy to false
endstruct

function shouldIEatThis(edible: Edible)
    print(edible->number + "x " + edible->name + "? ")

    if edible->healthy == true
        print("Yes, absolutely!")
    else
        print("Oh no, I'd rather not")
    endif

    print("\n")
end

set apple to Edible(name = "Apple", number = 2, healthy = true)
set pizza to Edible(name = "Pizza", number = 5)

set myEdibles to list(apple, pizza)

for edible in myEdibles
    shouldIEatThis(edible)
endfor
```
This will output
```pseudo
2x Apple? Yes, absolutely!
5x Pizza? Oh no, I'd rather not
```

# Exectution
To use the interactive mode, invoke the interpreter:
```terminal
dotnet run
```
Exit the interactive mode with the exit command.
pssp can interpret files:
```pseudo
dotnet run examples/simple.pssp
```
