# Python interview questions: Part 1

## Language
### Python 2 vs 3
* print is a key word in Python 2; In Python 3 its a function
* Python 3 supports unicode
* xrange: In Python 3, the range() was implemented like the xrange() function so that a dedicated xrange() function does not exist anymore (xrange() raises a NameError in Python 3).


### What does keyword pass mean?
pass is used as a placeholder for empty block / code
### Do arguments in Python get passed by reference or by value?
Immutable arguments are effectively passed by value. Objects such as integers and strings are passed by object reference instead of by copying, but because you can't change immutable objects in place anyhow, the effect is much like making a copy.
### What are list comprehensions?
A shorthand way to iterate over a list and perform operation on each element and product a new list
### list.append vs list.extend
Append takes one element and adds it to the end of the list; Extend does the same with a list, instead of a single element
### Can you change a string in place in Python?
No. Stings are immutable in Python
### What do you know about Python GIL?
Its a nasty thing. GIL stands for Global Interpreter Lock, which is used to safely modify data structures. Given Python is a dynamic typed language, when a thread changes a variable or data structure, it needs to be locked so that other thread or process can not make changes to it simultaneously.
In CPython, the global interpreter lock, or GIL, is a mutex that prevents multiple native threads from executing Python bytecodes at once. This lock is necessary mainly because CPython's memory management is not thread-safe.
### What does dir(Object) return?
the object's attributes names, the names of its class's attributes (methods, variables, ... )
### What is monkey patching and what is it used for?
Monkey patching is the dynamic replacement of an objects variables or code at runtime. Some uses for monkey patching are: mocking an objects code for testing / stubbing purposes; Replacing one implementation of code with another for specific functions. For example, synchronous code can be made to work in by monkey patching the synchronous pieces of the code.
### What is the meaning of `*args` and `**kwargs`?
`*args` and `**kwargs` are used for passing / capturing extra arguments and keyword arguments
### What is a decorator?
Decorators provide a simple syntax for calling higher-order functions. By definition, a decorator is a function that takes another function and extends the behavior of the latter function without explicitly modifying it.
### What is an iterator? generator? and differences?
Objects objects which can be used with a for loop are called iterable objects and support iterator protocol. Generators simplifies creation of iterators. A generator is a function that produces a sequence of results instead of a single value. generator uses yield keyword.
### How does garbage collector work?
Maintain reference count.: or every object, there is a count of the total number of references to that object. If that count ever falls to 0, then you can immediately deallocate that object because it is no longer live.

Periodically detect reference cycles: Deallocating when the reference count falls to 0 doesn’t work for all cases. Consider two objects A and B, where A holds a reference to B and B holds a reference to A. This is called a reference cycle. It could be the case that these are no longer live and so that both A and B should be garbage collected. However, the reference count on both objects are not zero, so they remain alive. To get around this, CPython uses an algorithm for detecting reference cycles and deallocating objects in the cycle.

Performance is enhanced with heuristics: Objects that have been created recently are more likely to need to be garbage collected. CPython introduces the concept of a generation to account for the relative age of an object. Younger generations have objects that have more recently been created and older generations hold objects that are less recent. Each object belongs to exactly one generation. When garbage collection is performed, CPython tries to garbage collect younger generations. Periodically, CPython will perform garbage collection on older generations (the rate at which this happens is determined by a heuristic).
### Explain variable scope in Python.
LEGB Rule.
L, Local — Names assigned in any way within a function (def or lambda)), and not declared global in that function.
E, Enclosing-function locals — Name in the local scope of any and all statically enclosing functions (def or lambda), from inner to outer.
G, Global (module) — Names assigned at the top-level of a module file, or by executing a global statement in a def within the file.
B, Built-in (Python) — Names preassigned in the built-in names module : open,range,SyntaxError,...

## Ecosystem
### What is pip used for?
Pip is used for installing Python packages.
### What tools do you use for linting, debugging and profiling?
Linting: pylint, ...
Debugging: pdb, print, ...
Profiling: cprofile, mprofile, ...
### What is the purpose of setup.py / setuptols?
They are used for creating / distributing / installing Python packages.
### What is the purpose of requirements.txt?
For storing the module dependencies for a project / module
### Have you used a virtualenv and why?
For creating isolated python environments for purposes like isolated testing, dependency management
### What is the purpose of PYTHONPATH?
PYTHONPATH stores the list of directories where Python code / modules can be found
### What are your favorite Python libraries?
list of Python modules
### Have you used iPython?
If yes, its used for data sciencey stuff for working with data, plotting charts, etc ...
### What are different implementations of Python and their uses?
CPython is the default. PyPy is another. IPython, Jython, Grumpy are intended to make Python work with various languages (.Net, Java, Go)

## Web
* How do you implement a web server in Python? What is WSGI?
Using WSGI. WSGI is a specification, laid out in PEP 333, for a standardized interface between Web servers and Python Web frameworks/applications. The goal is to provide a relatively simple yet comprehensive interface capable of supporting all (or most) interactions between a Web server and a Web framework.
* Name some web frameworks in Python.
Django, Flask, Bottle, Twisted, Tornado, ...

## Miscellaneous
* Explain negative / backwards indexing in Python.
* What is the difference between lists and tuples?
Lists are mutable where as tuples are immutable.
* Explain the difference between shallow copy vs deep copy
Shallow copy makes copy of data structures at the top level and links to the non-top level objects. Only top level objects are duplicated. Deep copy duplicates all the objects.
* When does a shallow copy change with out being modified directly?
When any of the non top-level object changes, shallow copy is modified
* What is the use of range() function?
To iterate over an object, typically in a for loop.
