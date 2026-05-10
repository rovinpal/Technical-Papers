# Python Technical Paper

## Arrays (Lists)

In Python, what most languages call an array is called a list. It holds multiple items in one variable in order.

Example: `fruits = ["apple", "banana", "cherry"]`

### The methods you'll actually use:

`append(item)` — adds an item to the end of the list.

fruits.append("mango")
```["apple", "banana", "cherry", "mango"]```


`insert(index, item)` — adds an item at a specific position.

fruits.insert(1, "kiwi")
```["apple", "kiwi", "banana", "cherry"]```

`remove(item)` — removes the first match it finds.

fruits.remove("banana")
```["apple", "cherry"]```

`pop(index)` — removes and returns the item at that index. No index? removes the last one.

fruits.pop(0)
```returns "apple", list is now ["banana", "cherry"]```

`sort()` — sorts the list alphabetically or numerically, in place.

nums = [3, 1, 4, 1, 5]
nums.sort()
```[1, 1, 3, 4, 5]```

`reverse()` — flips the list backwards, in place.

fruits.reverse()
```["cherry", "banana", "apple"]```

`index(item)` — returns the position of the first match.

fruits.index("banana")
```1```

`count(item)` — counts how many times something appears.

nums = [1, 2, 2, 3]
nums.count(2)
```2```

`clear()` — empties the whole list.

fruits.clear()
```[]```

`copy()` — returns a copy so you don't mess with the original.

new_list = fruits.copy()
new_list.append("mango")
```fruits is unchanged```

`len()` — not a list method but used all the time. returns the length.

len(fruits)
```3```


## Strings

A string is just text. Strings can't be changed in place — every method returns a new string.

Example: `name = "hello world"`

### The methods you'll actually use:

`upper()` / `lower()` — changes the case.

"hello".upper()  
```"HELLO"```

"HELLO".lower()  
```"hello"```

`strip()` — removes whitespace from both ends.

"  hello  ".strip()
```"hello"```

`split(separator)` — breaks the string into a list.

"a,b,c".split(",")
```["a", "b", "c"]```

`join(list)` — opposite of split. joins a list into one string.

" ".join(["hello", "world"])
```"hello world"```

`replace(old, new)` — swaps one part of the string for another.

"hello world".replace("world", "python")
```"hello python"```

`find(substring)` — returns the index of the first match, -1 if not found.

"hello world".find("world")
```6```

`startswith()` / `endswith()` — returns True or False.

"report.pdf".startswith("report")  
```True```

"report.pdf".endswith(".pdf")     
```True```

`count(substring)` — counts how many times something appears.

"banana".count("a")
```3```

`in` — checks if something is inside a string.

"py" in "python"
```True```

f-strings — the easiest way to put variables inside strings.

name = "Alex"
age = 25
print(f"my name is {name} and i am {age} years old")
```"my name is Alex and i am 25 years old"```


## Objects and Object-Oriented Programming (OOP)

OOP is a way of organizing your code around things (objects) instead of just functions. Think of it like a blueprint and a house — the blueprint is the class, and the house is the object (also called an instance).

```
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def bark(self):
        print(f"{self.name} says woof!")

my_dog = Dog("Rex", 3)
my_dog.bark()  # Rex says woof!
```

`__init__` runs automatically when you create a new object. `self` just refers to the current object — every method needs it as the first argument.

The four main ideas behind OOP:

**Encapsulation** — keep data and the methods that use it inside the same class. Add `__` before an attribute to make it private so outside code can't touch it directly.

**Inheritance** — a child class can inherit everything from a parent class and add its own stuff on top.

```
class Animal:
    def breathe(self):
        print("breathing")

class Dog(Animal):
    def bark(self):
        print("woof")

d = Dog()
d.breathe()  # works because Dog inherits from Animal
```

Use `super().__init__()` inside the child's `__init__` to also run the parent's setup.

**Polymorphism** — different classes can have a method with the same name and each does it their own way. So you can loop over a mix of objects and just call `.speak()` on all of them without caring what type they are.

**Abstraction** — hide the complex stuff inside the class and only expose what the user needs. They use the object without needing to know how it works inside.


## Decorators

A decorator is a function that wraps another function to add behavior before or after it runs, without changing the original function's code. The `@` symbol is just shorthand for applying it.

```
def shout(func):
    def wrapper():
        print("starting...")
        func()
        print("done.")
    return wrapper

@shout
def greet():
    print("hello!")

greet()
# starting...
# hello!
# done.
```

If the function takes arguments, use `*args` and `**kwargs` in the wrapper so they get passed through.

The three built-in decorators you'll see a lot:

`@staticmethod` — a method that doesn't need `self`. It's just a regular function living inside a class for organization.

`@classmethod` — gets the class itself as `cls` instead of an instance. Used to create alternative ways to build an object.

`@property` — lets you call a method like it's a plain attribute, no parentheses needed. Good for computed values.

```
class Circle:
    def __init__(self, radius):
        self.radius = radius

    @property
    def area(self):
        return 3.14 * self.radius ** 2

c = Circle(5)
print(c.area)  # 78.5 — no () needed
```


## virtualenv

`virtualenv` creates an isolated Python environment for your project so packages don't clash between projects. Project A might need `django==3.2` and project B might need `django==4.2` — virtualenv keeps them separate.

```
pip install virtualenv   # install once
virtualenv venv          # create the environment
source venv/bin/activate # activate it (Mac/Linux)
venv\Scripts\activate    # activate it (Windows)
```

Your terminal will show `(venv)` when it's active. Anything you install now stays inside this environment only. To leave it just run `deactivate`.

Save your dependencies so others can recreate your setup:
```
pip freeze > requirements.txt
pip install -r requirements.txt  # install from that file
```


## pip Package Manager

`pip` is Python's package installer. It downloads packages from PyPI, which is basically a huge library of free Python tools anyone can publish to.

```
pip install requests              # install a package
pip install requests==2.28.0      # install a specific version
pip install --upgrade requests    # upgrade to the latest version
pip uninstall requests            # remove a package
pip list                          # see everything installed
pip show requests                 # info about a specific package
pip list --outdated               # see what needs updating
```

Always use pip inside a virtual environment. On some systems you'll need `pip3` to make sure it targets Python 3.


## PEP-8 Standards

PEP-8 is Python's style guide. It doesn't change how your code runs — it just makes it easier to read.

**Indentation** — 4 spaces per level, never tabs.

**Line length** — keep lines under 79 characters.

**Imports** — always at the top of the file, one per line, grouped: standard library first, then third-party, then your own files, with a blank line between each group.

**Naming:**
- variables and functions: `snake_case`
- classes: `PascalCase`
- constants: `ALL_CAPS`
- private things: `_leading_underscore`

**Spaces** — put spaces around operators like `=`, `+`, `==`. No spaces inside brackets.

**Comparisons** — use `if thing:` not `if thing == True:`. Use `is None` not `== None`.

**Comments** — explain why, not what. The code already shows what's happening.

**Docstrings** — use triple quotes to describe what a function does.

```
def add(a, b):
    """returns the sum of a and b"""
    return a + b
```

You can check your code with `flake8` — run `pip install flake8` then `flake8 yourfile.py` and it'll point out every style issue.
