# Python Technical Paper

## Arrays (Lists)

In Python, what most languages call an array is called a list. It holds multiple items in one variable in order. Lists are mutable — meaning you can change them after creating them.

Example: `fruits = ["apple", "banana", "cherry"]`

### The methods you'll actually use:

* `append(item)` — adds an item to the end of the list.

fruits.append("mango")
```["apple", "banana", "cherry", "mango"]```


* `insert(index, item)` — adds an item at a specific position.

fruits.insert(1, "kiwi")
```["apple", "kiwi", "banana", "cherry"]```


* `remove(item)` — removes the first match it finds.

fruits.remove("banana")
```["apple", "cherry"]```

* `pop(index)` — removes and returns the item at that index. No index? removes the last one.

fruits.pop(0)
```returns "apple", list is now ["banana", "cherry"]```


* `sort()` — sorts the list alphabetically or numerically, in place.

nums = [3, 1, 4, 1, 5]
nums.sort()
```[1, 1, 3, 4, 5]```


* `reverse()` — flips the list backwards, in place.

fruits.reverse()
```["cherry", "banana", "apple"]```


* `index(item)` — returns the position of the first match.

fruits.index("banana")
```1```


* `count(item)` — counts how many times something appears.

nums = [1, 2, 2, 3]
nums.count(2)
```2```


* `clear()` — empties the whole list.

fruits.clear()
```[]```


* `copy()` — returns a copy so you don't mess with the original.

new_list = fruits.copy()
new_list.append("mango")
```fruits is unchanged```


* `len()` — not a list method but used all the time. returns the length.

len(fruits)
```3```


---

## Tuples

A tuple is like a list but you can't change it once it's created. That's called immutable. Use `()` instead of `[]`. Because it can't be changed it's faster and safer for data that shouldn't be modified.

Example: `point = (10, 20)`

You can still access items by index, you just can't add, remove, or change them.

point[0]
```10```

point[1]
```20```

If you try to change a value it'll crash:
```# point[0] = 99  <- TypeError, tuples can't be changed```

A common use case is returning multiple values from a function:
```python
def get_dimensions():
    return (1920, 1080)

width, height = get_dimensions()
```

---

## Sets

A set holds unique items only — duplicates are removed automatically. The order doesn't matter and you can't access items by index. Use `{}`.

Example: `nums = {1, 2, 2, 3, 3}`

```{1, 2, 3}  # duplicates are gone```

### The methods you'll actually use:

* `add(item)` — adds an item to the set.

nums.add(4)
```{1, 2, 3, 4}```

* `remove(item)` — removes an item. raises an error if it doesn't exist.

nums.remove(1)
```{2, 3, 4}```

* `discard(item)` — same as remove but won't crash if the item isn't there.

nums.discard(99)
```nothing happens```

* `union(set)` — combines two sets, no duplicates.

{1, 2, 3}.union({3, 4, 5})
```{1, 2, 3, 4, 5}```

* `intersection(set)` — returns only the items that exist in both sets.

{1, 2, 3}.intersection({2, 3, 4})
```{2, 3}```

* `in` — the main way to check if something is in a set (very fast).

3 in {1, 2, 3}
```True```

---

## Dictionaries

A dictionary stores key-value pairs. Think of it like a real dictionary — the word is the key and the definition is the value. Use `{}` with colons.

Example: `person = {"name": "Alex", "age": 25}`

Access a value by its key:

person["name"]
```"Alex"```

Add or update a value:

person["age"] = 26
```{"name": "Alex", "age": 26}```

### The methods you'll actually use:

* `get(key)` — returns the value for a key. returns None if the key doesn't exist instead of crashing.

person.get("name")
```"Alex"```

person.get("email")
```None```

* `keys()` — returns all the keys.

person.keys()
```dict_keys(["name", "age"])```

* `values()` — returns all the values.

person.values()
```dict_values(["Alex", 26])```

* `items()` — returns all key-value pairs. great for looping.

for key, value in person.items():
    print(key, value)
```name Alex  /  age 26```

* `pop(key)` — removes a key and returns its value.

person.pop("age")
```returns 26, key is removed```

* `in` — check if a key exists in the dictionary.

"name" in person
```True```

---

## Range

`range()` generates a sequence of numbers. You'll use it constantly in for loops. It doesn't actually create a list — it generates numbers one at a time which makes it memory efficient.

range(5)
```0, 1, 2, 3, 4  — starts at 0 by default```

range(1, 6)
```1, 2, 3, 4, 5  — start, stop (stop is not included)```

range(0, 10, 2)
```0, 2, 4, 6, 8  — start, stop, step```

Most common use — looping a set number of times:

```python
for i in range(3):
    print(i)
# 0
# 1
# 2
```

If you need an actual list from it, wrap it in `list()`:

list(range(5))
```[0, 1, 2, 3, 4]```

---

## Strings

A string is just text. Strings are also a sequence type — just like lists and tuples — which is why slicing works the same way on all of them. Strings can't be changed in place — every method returns a new string.

Example: `name = "hello world"`

Slicing works the same as lists:

name[0:5]
```"hello"```

name[::-1]
```"dlrow olleh"  — reversed```

### The methods you'll actually use:

* `upper()` / `lower()` — changes the case.

"hello".upper()  
```"HELLO"```

"HELLO".lower()  
```"hello"```


* `strip()` — removes whitespace from both ends.

"  hello  ".strip()
```"hello"```


* `split(separator)` — breaks the string into a list.

"a,b,c".split(",")
```["a", "b", "c"]```


* `join(list)` — opposite of split. joins a list into one string.

" ".join(["hello", "world"])
```"hello world"```


* `replace(old, new)` — swaps one part of the string for another.

"hello world".replace("world", "python")
```"hello python"```


* `find(substring)` — returns the index of the first match, -1 if not found.

"hello world".find("world")
```6```


* `count(substring)` — counts how many times something appears.

"banana".count("a")
```3```


* `in` — checks if something is inside a string.

"py" in "python"
```True```

* f-strings — the easiest way to put variables inside strings.

name = "Alex"
age = 25
print(f"my name is {name} and i am {age} years old")
```"my name is Alex and i am 25 years old"```



## Objects and Object-Oriented Programming (OOP)

OOP is a way of organizing your code around things (objects) instead of just functions. Think of it like a blueprint and a house — the blueprint is the class, and the house is the object (also called an instance).

```python
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

```python
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

```python
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

```python
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

```bash
pip install virtualenv   # install once
virtualenv venv          # create the environment
source venv/bin/activate # activate it (Mac/Linux)
venv\Scripts\activate    # activate it (Windows)
```

Your terminal will show `(venv)` when it's active. Anything you install now stays inside this environment only. To leave it just run `deactivate`.

Save your dependencies so others can recreate your setup:
```bash
pip freeze > requirements.txt
pip install -r requirements.txt  # install from that file
```



## pip Package Manager

`pip` is Python's package installer. It downloads packages from PyPI, which is basically a huge library of free Python tools anyone can publish to.

```bash
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

```python
def add(a, b):
    """returns the sum of a and b"""
    return a + b
```

You can check your code with `flake8` — run `pip install flake8` then `flake8 yourfile.py` and it'll point out every style issue.
