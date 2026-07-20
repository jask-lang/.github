# A secure way of scripting
jask is a highly readable and safe interpreted language in early development. The interpreter is fully written in C# without other dependencies.
It is a hobby project for fun and learning, so contributions are always welcome!

A brief summary of the features of jask:
* :star: dynamically typed variables (variables are just a container for any kind of data)
* :muscle: strongly typed values (jask enforces strict type checking)
* :lock: fully immutable (things in jask cannot mutate themselves, operations always creating copies)
* :construction: data and behaviour are separated (functions are not bound to anything, data is held separated)

jask is designed as a language that always prioritizes **explicit** actions over **implicit** ones. Code is always executed deterministically and, by default, runs without permissions for input and output or read and write access at the file level. Permissions must be explicitly passed to the interpreter before each execution. This ensures that unknown code can only perform limited actions in a sandbox, imagine *never trust, always verify*.

Dive right into? Find the interpreters implementation [here](https://github.com/jask-lang/interpreter). A collection of useful functions written completely in jask can be found at [jcore](https://github.com/jask-lang/jcore). Want syntax highlightning for your IDE? [We got you](https://github.com/jask-lang/syntax-highlighting).

# Try jask out!
Invoke the interactive mode directly in a terminal:
```terminal
dotnet run --allow-stdout
```
Or pass a file:
```terminal
dotnet run --allow-stdout --input="example.jask"
```
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
Be sure to pass *--allow-stdout* to the interpreter in order to use the *print* function.
