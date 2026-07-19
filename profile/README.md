jask is a highly readable and safe interpreted language in early development. The interpreter is fully written in C# without other dependencies. It is just a hobby project for fun and learning, contributions are always welcome!

The main goal is to keep the interpreter itself as small as possible and to implement only those functions internally that are truly necessary or that greatly affects performance.
All other functions should be written directly in jask to explore and expand the language's capabilities.
A brief summary of the properties:
* dynamically typed variables (Variables are just a container for any kind of data)
* strongly typed values (jask enforces strict type checking)
* fully immutable (things in jask cannot mutate themselves, operations always creating copies)
* data and behaviour are separated (functions are not bound to anything, data is held separated)

A collection of useful functions written in jask can be found at [jcore](https://github.com/jask-lang/jcore).

# Now show me some code...

```python
struct Edible
    set name    = ""
    set number  = 0
    set healthy = false
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

set apple = Edible(name = "Apple", number = 2, healthy = true)
set pizza = Edible(name = "Pizza", number = 5)

set myEdibles = list(apple, pizza)

for edible in myEdibles
    shouldIEatThis(edible)
endfor
```
This will output
```pseudo
2x Apple? Yes, absolutely!
5x Pizza? Oh no, I'd rather not
```
