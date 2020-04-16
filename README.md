# A small simple guide to learn Python:

Adapted from the NSA Guide to Python Programming. Seriously if you want something more comprehensive, and you like reading courses, check it out at:
https://archive.org/details/comp3321/page/n89/mode/2up/search/device

### Adapted by: Bruno M. Cervantes Quino

### V1.01

### Installing Python (and Jupyter notebooks) via Anaconda.

1) Download Anaconda
https://www.anaconda.com/distribution/

2) Install it! It's quite simple ....

3) Load Anaconda Navigator and click on Jupyter Notebook

4) Use the Jupyter navigator (It should have loaded into your browser... like Chrome) and navigate until you are in the directory you wish to use. Then click new and choose Python 3. Voila you created your first notebook.


### Installing a Package.

Maybe, you'll find that you need to import a module, but Python doesn't have it. Very simple remedy!

For Windows:

1) Go into Anaconda Navigator and click on 'CMD.exe Prompt'

2) Inside the command line type:

```python
pip install name_of_package

pip3 install name_of_package # ONLY if you have Python 3 and Python 2

```

For Mac OS / Linux:

1) Go to your terminal.

2) Inside the terminal type:

```python
pip install name_of_package

pip3 install name_of_package # ONLY if you have Python 3 and Python 2

```

## Types of Data:

Some basic types of data you'll work with (as you can imagine there are plenty more!)


### Numerics:


```python
1234 # This is an Integer! Any Positive or Negative number.

1.34565667 # This is a Float! Any decimal number (as well as scientific notations)
```

### Non-Numeric:


```python
"Hello 1234!" ## This is a string! It can have any character, both letters, numbers and other symbols!
```

### Boolean


```python
True
False
#(1 and 0 respectively)
```

## Creating variables:
Usually when you type some information, you plan to reuse it. This is why variables exist!


```python
test = "Hello"
test2 = 123
test3 = True

print(test)
print(test2)
print(test3)
```

## Basic flow control:

### IF, ELSE (and elif)
Change the variable (x) to see how the flow changes!


```python
x = 5

if x > 4:
    print("Greater than 3")
elif x == 2:
    print("Equal to 2")
else:
    print("No condition is met!")



```

### While loops:
#### CAREFUL, be sure your closing condition is met! Otherwise it will be an infinite loooooop


```python
x = 0
while x != 10:
    print(x)
    x+= 1 ### take this one out and you'll be printing 0 forever! (or run out of memory, whichever occurs first)
```

### For loops:


```python
x = [0,1,2,3] # this is a list, we will cover this later.
for n in x:
    print()
```

## Tad more advanced flow control:

### CONTINUE clause:
Returns the flow to the beginning of the while loop. The continue statement rejects all the remaining statements below it


```python
i = 0
while(True):
    i += 1
    if (i ==5):
        continue # take this line out to see what happens
        print("I will never be printed")   
    print(i)
    if(i == 8):
        break

```

### BREAK clause
Terminates the flow.


```python
i = 0
while(True):
    i += 1
    print(i)
    if (i == 8):
        break
```

### For Loop with range function.
range() creates the integer numbers between the given start integer to the stop integer.


```python
b = range(0,10,1) # from 0 to 10 (not inclusive) in steps of 1
b[0] ## first
b[-1] ## last
```


```python
for i in range(10,20,2): ##From 10 to 20(not inclusive) in steps of 2
    print(i)
```


```python
for i in range(100,0,-10): ##From 100 to 0 (not inclusive) in steps of -10
    print(i)   
```

### Strings are actually sequences!


```python
a="pepe"
for i in range(len(a)):
    print("The character at position " + str(i) + " is " + a[i])
```


```python
a="pepe"
for (i,j) in enumerate(a): ## this version is preferable
    print("The character at position " + str(i) + " is " + j)
```

### Example:
Note: This is a function (noted by the def. You'll learn about making them soon(TM)


```python
def shout_words(string):
    if (type(string) != str):
        print("Not string")
    else:
        for x in string.split(" "):
            print(x.upper())

shout_words("hello all") # Feel free to change this
```

### Example 2:


```python
def extract_longer(nu,x):
    lista = x.split(" ")
    lista_final=[]
    for x in range(len(lista)):
        if len(lista[x]) != nu:
            pass
        else:
            lista_final.append(lista[x])
    if not lista_final:
        return False
    else:
        print(lista_final)

extract_longer(2, "hola tue sir ella")   # Feel free to change this       
```

## Python Lists:
Lists are a type of collection which is ordered and changeable. Allows duplicate members.


```python
fruit = ['Apple','Orange','Pear','Lime'] # creates a list

fruit.append('Banana') ## appends this to the end

fruit.insert(3,'Cherry') ## inserts into position 3 (aka 4)

fruit.append(['Apple','lemon']) ### It will append this list inside the list so that ... 'Banana', ['Kiwi', 'Apple']]

fruit.extend(['Apple','lemon']) ### it will extend the list to include this list (basically an append for multiple items)

fruit.remove('Apple') ### removes the first instance of 'Apple'

fruit.pop() # shows the n item, using nothing acts like a .first()

fruit + fruit ## + acts like an .extend()

len(fruit) # number of elements in list

'Apple' in fruit  # True, but one thing, if you had apple in your nested list, it will give out FALSE

fruit.count('Apple') # 1. but like the line above, it doesn’t count nested list inside list

fruit.index('Apple',1,7) # returns position of index of the first item whose value is equal to Apple. You can add 2 parameters the index number to start and the index number to finish your search
```

### List comprehension AKA fancy, more efficient way to do 'for loops'


```python
[i for i in range(10)] #[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

[[i,i*2,i**2] for i in range(5)] # [[0, 0, 0], [1, 2, 1], [2, 4, 4], [3, 6, 9], [4, 8, 16]]

[[i,i*2,i**2] for i in range(10) if i % 2 == 0]  # [[0, 0, 0], [2, 4, 4], [4, 8, 16], [6, 12, 36], [8, 16, 64]]

[[i+j for i in 'ab'] for j in 'def'] # [['ad', 'bd'], ['ae', 'be'], ['af', 'bf']]
```

### Sorting and reordering.


```python
lista = ['uno', 'dos', 'tres'  ]
sorted(lista) ## sorts from a to z, returns a new list
lista.sort() ## mutates the current list in place.

# you can also reverse the order of a list.
list(reversed(lista)) ### reversed returns an iterator, you need to explicitly convert it back to list

# a list contains a number of objects in a specific order VS  an iterator yields a number of objects in a specific order
# a list of a trillion integers would use more memory than most machines have available, which makes the iterator much more efficient ... at the cost of not being able to ask for an object somewhere in the middle
```

### Slight detour to yield
You use yield to iterate over long sequences and you don’t want to charge everything into Memory (or need more control)


```python
def pepe(n):
    for x in range(n):
        yield x
a = pepe(3)
next(a) # yields  0
#next(a) # yields  1
##next(a) # yields  2
###next(a) # Error! StopIteration.

#### Try taking the # from the statements and run the cell again!
#### Using Yield allow you to create a function that can iterate over humongous amounts of data (even infinite) since it only loads a vale at a time.
#### If you try to do this with return and a very big number... you will run out of memory.
```

## Tuples:
An immutable python list. Thus, you cannot use methods that changes in-place the list.


```python
tupla = ('a','b','c')

new_tupla = tupla + tupla ### you can however concatenate tuples to create a new one out of existing ones.

new_tupla # But again this is a new object the original one  hasn’t changed.

```

## Slicing and Index:
These operations exists for any sequence!


```python

weh = ('a','b','c','d','e','f')
weh[1] # b
weh[1:3] # b, c
weh[3] in weh[1:3] # false, position 3 doesn’t exist in that slice of weh
weh[:3] # a,b,c
weh[3:] # d,e,f
weh[0:5:2] # a, c, e steps of 2
weh[::-1] # f,e,d,c,b,a

```

## Dictionary AKA key-value pairs:
REMEMBER the keys must be unique!


```python
veggies = {'broccoli': 1, 'rhubarb':2}

veggies['spinach'] = 3  ## adds in the same list the key value pair
del veggies['rhubarb'] ## deletes the value in the dictionary
veggies.update({'lettuce':4}) ## same as above

'spinach' in veggies # true (you search the key)
3 in veggies # False you only search the key not the value
veggies['spinach'] # 3 HOWEVER HOWEVER DONT USE THIS IT MIGHT THROW AN ERROR IF THE KEY DOESNT EXIST
veggies.get('spinach') # use this instead
veggies.get('rhubarb') # returns None
veggies.get('rhubarb',2) # returns the value of the key value you just searched, but your dictionary is unchanged
veggies.clear() # Empties the dictionary
```

## Sets and FrozenSets:
A collection which is unordered and unindexed. No duplicate members.


```python
#Adding something already there will do nothing (but no errors)
## 2 sets are equal if they contain the same items, regardless of order
number = set([2,3,4,5,6,7])

### frozensets are the same but immutable
number_f = frozenset([1,2,3,4,5])

##Special operations
set_a = set(['one','two','three'])
set_b = set(['one','four','five'])

set_a & set_b ## 'one' the intersection
set_a | set_b ## 'five', 'four', 'one', 'three', 'two'  the union
set_a ^ set_b ## 'five', 'four', 'three', 'two' the symmetric difference aka all that doesn’t intersects
set_a - set_b ## 'five', 'four', 'three', 'two' the asymmetric difference aka everything in a that's not in b

```

## File Input and Output

### Basic example to write into a file


```python
myfile = open('data.txt', 'w' ) #don’t forget that if the file is in another directory put the path!'
myfile.write("wololo")  ## Opening a file that already exists will erase the original file
myfile.close()
```

#### There are different modes: 'r' reading, 'a' appending, 'r+' reading and writing and 'b' binary mode

### A way to use a file in a block is using 'with':


```python
with open('data.txt') as f:
    print(f.read())
```

### Using writelines


```python
with open('data2.txt', 'w') as f:
    f.writelines("first\n")
    f.writelines(["second\n", "third\n"])    
with open('data2.txt') as f:
    print(f.read())
```

### How to read line by line without loading everything into memory:


```python
with open('data2.txt') as reader:
    for line in reader:
        print(line.strip()) #### strip() removes new lines and whitespaces
```

### The tell and seek methods:
The tell method returns the current position of the cursor within the file.
The seek command sets the position of the cursor within the file


```python
inputfile = open('data2.txt','r')
inputfile.tell() # tells 0
inputfile.read(4) ## reads 4 chars
inputfile.tell() # tells 4 now, meaning that if you execute read() you’ll get all the characters after the first 4.
inputfile.seek(0) # returns to position 0 of the file, meaning that you'll read since the beginning
inputfile.read()  # reads everything, to prove that seek works.
inputfile.close()
```

### File like objects
A very useful module to make a string into a file like object is called StringIO, it takes a string and give it file methods like read and write.


```python
import io

mystringfile = io.StringIO()   # for handing bytes use io.BytesIO
mystringfile.write("this is my data") # We just wrote to the object, not a file.
mystringfile.read() ## Cursor is currently at the end after the write we performed.
mystringfile.seek(0) ## Now we are back at position 0
mystringfile.read()  ## proof
mystringfile = io.StringIO("MyData") ## this would create the object with data inside and initiate at position 0



```

#### Pretend we have a function that expects to read data from a file before it operates.


```python
def iprintdata(x):
    print(x.read())
#iprintdata("wololo") ### won’t work, it’s a string.
my_io = io.StringIO('wololo')
iprintdata(my_io)
```

## OBJECT Orienteering:

### Your first class:


```python
class Person(object):
    pass
nobody = Person()
type(nobody) ## type Person!
```


```python
class Person(object):
    species = "Homo sapiens"
    def talk(self): # remember to give every method at least an argument (almost always self). Python Internally translate nobody.talk() into Person.talk(nobody)
        return "Hello!"

nobody = Person()
nobody.species # 'Homo sapiens'
nobody.talk() # 'Hello!'

# You can assign and re assign data attributes
nobody.name = "Ashens" # new attribute!
nobody.species = "Human" # reassigned
nobody.species #Human
nobody.name # Ashens
del nobody.name # deleted
#nobody.name # AttributeError! no longer exists
```

### Of course, it’s better if you assign instance specific attributes if you are gonna keep adding them every time.
You create these attributes using the __innit__ function.


```python
class Person(object):
    species = "Homo sapiens"
    def __init__(self, name="Unknown", age=18):
        self.name = name
        self.age = age
    def talk(self):
        return "Hello! My name is {}.".format(self.name)
```


```python
ashens = Person("Ashens", 38)
ashens.name
ashens.age
```


```python
# Dynamic allocations of __str__ and __repr__
# To control how your object is printed, implement '__str__' and to control how it looks as an output from the interactive interpreter, implement "__repr__"
```


```python
def person_str(self):
    return "Name: {0}, Age:{1}".format(self.name, self.age)
Person.__str__ = person_str
def person_repr(self):
    return "Person('{0}','{1})'".format(self.name, self.age)
Person.__repr__ = person_repr

```


```python
print(ashens) ## before it was something like <__main__.Person object at 0x000001CDD78EDE88>
```


```python
ashens  ## before it was something like <__main__.Person at 0x1cdd78ede88>
```

### Nevertheless, in practice we rarely do this (just because you can, doesn’t mean you should). SO instead the class should be initiated like this:


```python
class Person(object):
    species = "Homo sapiens"
    def __init__(self, name="Unknown", age=18):
        self.name = name
        self.age = age
    def talk(self):
        return "Hello! My name is {}.".format(self.name)
    def __str__(self):
        return "Name: {0}, Age:{1}".format(self.name, self.age)
    def __repr__(self):
        return "Person('{0}','{1})'".format(self.name, self.age)
    def __eq__(self, other):
        return self.age == other.age

rob = Person("Rob", 33)
frank = Person("Frank", 38)
rob2 = Person("Rob2", 33)

rob # Person('Rob','33)'
print(frank) # Name: Frank, Age:38
rob == frank #False
rob == rob2  # True
```

### Inheritance: A class created from an existing class


```python
class Student(Person):
    bedtime = 'Midnight'
    def work(self):
        import time
        print("Work")
        time.sleep(5)
        print("Fugggg")
tyler = Student("Tyler", 21)
tyler.species # 'Homo sapiens'
tyler.talk() # Hello! ....
tyler.work()
```

### Creating a python script with a class
The main thing... get it? IS that because you added the __name .... if you were to run this script in the cli, then it will execute, but if you import it as a module... you will just get the definitions and functions... but no execution


```python
class Awesome(object):
    def __init__(self,awesome_thing):
        self.thing = awesome_thing
    def __str__(self):
        return "{0.thing} is awesome!!!".format(self)

def cool(x):
    return "All is cool when you are part of {0}".format(x)

def main():
    potato= Awesome("Potato")
    potatoCoolio = cool(potato.thing)
    print(potato)
    print(potatoCoolio)  

if __name__ == '__main__':
    main()
```

## Namespace:
Are what store the name of all variables, functions, classes, modules, etc. Kind of like a big dictionary that maps the name to the things named

Global namespace: is accessible from everywhere in the program.

Local Namespace: Is accessible depending on the current scope - whether you are in a function, loop, class, etc. Also, each module has its own namespace.


```python
dir() # shows the names in the global namespace.
x = "pepe"
dir() # now x appears!
locals() == globals() # should be true, since we are not inside  a function or a loop.

```

## Exceptions:


```python
# for i in range(10) # invalid syntax... this happens when Python cannot parse what you typed.
# There are more exceptions!

import builtins
help(builtins) # there are a shitton
```

When an exception occurs, best option is to handle them and do something more than just exit and print to the screen.

Some exceptions are useful! like KeyboardInterrupt (means you pressed Ctr-C to kill an execution).

In python you do this with the try and except commands.


### Example 1:


```python
def f(x):
    try:
        print("I’m going to convert the input to an integer")
        print(int(x))
    except ValueError:
        print ("I am afraid i cannot do this john")

#To explain the logic behind this madness:
# Everything between try and except is executed
# If that produces no exceptions, except block is skipped and he program continues.
# if an exception occurs, the rest of the try block is skipped.
# If the type of exception is named after the except block, the code after except is executed
# Else the execution stops, and you have an unhandled exception
```

### Example 2:


```python

def f(x):
    try:
        print("I’m going to convert the input to an integer")
        print(int(x))
    except (ValueError, TypeError) as  detail:
        print ("handled exception", detail)
    except:
        print("unhandled exception!")
    finally:
        print("this will always run!")

# You can add multiple exceptions in an except command and using as allow us to capture it into a message.
# The ‘finally’ command will ALWAYS be executed, regardless of whether there was an exception or not.... So, use this to clean up anything left over from try and except.
# Note that in spite of this, having an auxiliary function to clean might be useful to be executed before running you main() As some errors cannot be caught (your server collapses and shuts down for example)
```

### Raising Exceptions:
Sometimes you will want to cause an exception and let someone else handle it. You use the raise command


```python
raise TypeError('Wrong type')
# If no inbuilt exception is suitable for what you want to raise, defining a new type of exception is as easy as creating  a  new class that inherits from the Exception type.
class myOwnError(Exception):
    pass
raise myOwnError("Wololo!")
```

#### Creating your own Iterator (Digression alert):
(Honestly for 95% of your work you will never see this, but hey it’s good to know right?)


```python


class NonFactorIterable(object):
    def __init__(self, *args):
        self.avoid_multiples = args
        self.x = 0
    def __next__(self):
        self.x += 1
        while True:
            if self.x > 200:  
                raise StopIteration ## this is a great way to handle an event that is not unexpected but requires termination
            for y in self.avoid_multiples:
                if self.x % y == 0:
                    self.x += 1
                    break
            else:
                return self.x
    def __iter__(self):
        return self

silent_fizz_buzz = NonFactorIterable(3, 5)

[x for x in silent_fizz_buzz]

weh = NonFactorIterable(2, 3, 5, 7, 11, 13, 17)

[x for x in weh]
```

#### Generators: iterators with a much lighter syntax. a very simple one looks like list comprehensions but with () instead of [].
#### More complicated generators are like functions except that you use yield instead of return (remember the slight detour i took earlier? Go back and check it :) )

## String Formatting:
Some basic examples

### Example 1:


```python
'This is a formatted string: {}'.format("hello, i am the formatted string")
```

### Example 2:


```python
'{2}, {0} and {1}'.format('meh', 'weh', 'eh')


```

### Example 3:


```python
'{who} is a {what}'.format(who = 'Rob', what='broccoli')


```

### Example 4:
Now with more lists (you can also use dictionaries):


```python
fruit = ['mango','tomato','apple']
'{0[2]} is a fruit'.format(fruit)
```

### f-string (Python 3.6+)
Expressions added directly inside the {}


```python
x = 34
y = 33
f"{x+y}"
```

## Functional Programming in Python


Warning, the following topic (as you'll see in the examples) is a bit more obtuse.
Moreover, Python is not really well optimised to do heavy programming the functional way... so while neat and good to know... you kinda can skip this part.


```python
### This is functional:
def increment(x):
    return x + 1
```


```python
# This is not:
a = 0
def increment():
    global a
    a += 1
```

#### Slightly more complex example:


```python
# This is functional:

def functionalEx(n):
    if n == 0:
        return 0
    else:
        return n + functionalEx(n - 1) # this is called recursion

functionalEx(4)   
```


```python
# This is not:
def notFunctionalEx(n):
    counter = n
    summation = 0
    while counter != 0: # while loops are never functional, as it depends on a variable that changes aka mutates for it to work
        summation += counter
        counter -= 1
    return summation

notFunctionalEx(4)  
```

### Recursion! How to loop without a loop aka without mutability

Again, remember my example? Here you don’t change a variable; you are merely calling the same function over and over again with an updated parameter


```python
def functionalEx(n):
    if n == 0:
        return 0
    else:
        return n + functionalEx(n - 1) # this is called recursion
```

The always classic Fibonacci number


```python
def nthFib(n):
    if n < 1:
        return 0
    elif n ==1:
        return 1
    elif n == 2:
        return 1
    else:
        return nthFib(n-2) + nthFib(n - 1)

nthFib(10)
```

#### Warning: Wall of text incoming

Note about recursion: Python is not optimised to be a functional programming language like Scala. For example, there is a recursion limit (1000 calls).

Remember, there is no universal programming language. if you needed strictly functional programming try Scala.

With that said, there is technically a workaround.... which is tail recursion (which in python is not optimized).

NOTE: For this to work you would need to create your own tail recursion class... which is beyond the scope of this guide
(But here is an example https://stackoverflow.com/questions/27417874/tail-recursion-optimization-decorator-in-python)


```python
#@tail_recursive
def functional_tailEx(n, accum = 0):
    if n == 0:
        return accum
    else:
        return functional_tailEx(n - 1, accum + n) # this is called tail recursion.

# functionalEx(4)
## 4 + functionalEx(4 - 1) -> 4 + (3 + functionalEx(3-1)) --> ...... -> 4 + (3 + ( 2 + (1 + (functionalEx(0)))) # n keeps increasing!!!!

# functional_tailEx(4)
## functional_tailEx(functional_tailEx(functional_tailEx(functional_tailEx(functional_tailEx(0))))) ### no n, you are merely calling the function over and over again with a bigger parameter accum


```

## Map and Reduce:
Technically this is still part functional programming, but this is more applicable for python than recursion and quite frankly is important to know.

### map: is a function that takes 2 arguments: another function and a collection of items. it will:
1) Run the function on each item of the original collection

2) Return a new collection containing the results (it’s an iterator so you need to convert it to something else to print it)

3) This leaves the original collection unchanged

### Example 1:


```python
name_lengths = map(len,['Mary','Isla','Sam'])
print(list(name_lengths)) # [4, 4, 3]
```

### Example 2:


```python
squares = map(lambda x: x * x, [0,2,3,4])
print(list(squares)) ## [0, 4, 9, 16]
```

##### What is lambda:
Lambda allows you to define an anonymous function. Arguments fit between lambda and : so, x is an argument. The stuff after the colon gets implicitly returned

I would use lambda functions for map (but ... if it’s  a very complex function i wouldn’t).For very simple cases or when you don’t need to reuse the function multiple times. Remember if you don’t save the results they are gone forever.

### Example 3:


```python
import random
names = ['Trump', 'Biden', 'Berney']
covernames = map(lambda x: random.choice(['COVFEFE','BEEEERN','UKRAINE']),names)
print(list(covernames))
```

### reduce: Follow-on counterpart to map  given a function and a collection of items, it uses the function to combine them into a single value:
Functions passed to reduce have some restrictions. It must take 2 arguments, an accumulator a and an update value u. u is like before with map, it will get set to each item in your collection one by one. a is new, it will receive the output from the previous function call, thus combining value from item to item


```python
import functools # for reduce
sum = functools.reduce(lambda a, u: a + u, [0,1,2,3,4])
print(sum)
```

## Command line Arguments:
Everything passed as Arguments to a Python program is available in the interpreter as the list of string in sys.argv


```python
import sys
print(sys.argv)

# When running a script, sys.argv[0] is the name of the script (since this is a Jupyter notebook, the notebook isn’t the python script so don’t get confused, rather it is argument 2)
# in theory you could parse this, but you’ll be limited to simple positional arguments
```

### The argparse Module
Your way to parse arguments other than simple positional ones


```python
import argparse
parser = argparse.ArgumentParser()
parser.add_argument('n')
parser.add_argument('-f')
parser.add_argument('-i', '--input')
parser.print_help()
args = parser.parse_args('abc -f xyz'.split())
args.f
```

Now copy this code below and save it into a test.py file.


```python
import argparse
parser = argparse.ArgumentParser()
parser.add_argument('n')
parser.add_argument('-f')
parser.add_argument('-i', '--input')
args = parser.parse_args()

print(args)

# Now go to your command line/terminal and execute the following commands:
#!python3 test.py -f hello hello2 --input=hello3.txt
#!python3 test.py -h

#What do you see?
```

### Advanced stuff:
The add_argument method can configure behaviour, such as making the parser attempt to convert arguments to the specified type like int or float or file (so long as it’s a single string argument)


```python
parser = argparse.ArgumentParser()
parser.add_argument('n', type=int)
parser.parse_args('5'.split()) ## Namespace(n=5)
```

The nargs keyword lets arguments specify a fixed or variable number of arguments to consume.

Giving nargs the vale '?' makes positional arguments optional, in which case the default keyword is required


```python
parser = argparse.ArgumentParser()
parser.add_argument('n', nargs=2)
parser.add_argument('-m', nargs='*') # arbitrary number arguments
parser.parse_args('n1 n2 -m a b c'.split()) # Namespace(m=['a', 'b', 'c'], n=['n1', 'n2'])
```


```python
parser.add_argument('o', nargs='?', default='meh') # arbitrary arguments
parser.parse_args('n1 n2 -m a b c'.split()) # Namespace(m=['a', 'b', 'c'], n=['n1', 'n2'], o='meh')
parser.parse_args('n1 n2 hue -m a b c'.split()) # Namespace(m=['a', 'b', 'c'], n=['n1', 'n2'], o='hue')
```

The default keyword can also be used with optional arguments. When an optional argument is always used as a flag without parameter, it is also possible to use the action='store_const' and const keyword.

In this case, when the option is detected, the Namespace is given an appropriately named attribute with const as its value. If the option is not present in the parsed args, the attribute is created with the value given in default or None if it isn’t set.

For more info https://docs.python.org/3.7/library/argparse.html


```python
parser = argparse.ArgumentParser()
parser.add_argument('-n', action='store_const', const=7) # again if the flag is given as an argument the constant value of 7 will be returned, if nothing is presented since there is no default None is returned
parser.add_argument('-b', action='store_true') # if the flag is given as an argument. true is returned else false
parser.add_argument('-c', action='store_const', const=5, default=3)

parser.parse_args([])  # Namespace(b=False, c=3, n=None)

parser.parse_args('-n -b'.split()) #Namespace(b=True, c=3, n=7)

parser.parse_args('-cbn'.split()) #Namespace(b=True, c=5, n=7)
```

## Logging:
The easiest way to look Pro... and make your life easier!
The logging module is included. Let’s start by writing messages at different levels.


```python
import logging
logging.warning("You have been warned")

logging.critical("ABORT ABORT ABORT")

logging.info('This is some info') ### this one may not appear! By default, the root logger is set to only handle messages Warning or higher.

logging.root.setLevel(logging.INFO)
logging.root.getEffectiveLevel() == logging.INFO
logging.info('This is some info that should now appear')

```

As you can see there are several levels, from least to most important: DEBUG, INFO, WARNING, ERROR, CRITICAL

The level of the root logger can be configured at module level but MUST be done before any messages are sent.

Otherwise the level must be set directly on the logger.

##### Try this in a New Session (it won’t work if you already displayed messages)


```python
import logging

logging.basicConfig(level=logging.INFO)
logging.info("this is some new info.")
logging.root.getEffectiveLevel() == logging.INFO

# INFO messages should appear without any setLevel
```

From all this, a strategy emerges around using logging to improve your debugging:

1) Instead of print statements, add calls to logging.debug to your code.

2) At the top of your script, use logging.basicConfig(level=logging.DEBUG) for development: switch to INFO or WARNING for production.

3) Optionally make a command line option for your script that enables debugging output(eg my_script.py --verbose)


#### Note there is much much more stuff you could do, like using multiple loggers at the same time, each handing its own formatting and levels. Again, this is just the tip.

## System interaction
os module: allows you to interact with your operating system.
#### For this part you might be better served copying the code into a .py file and running it on the shell


```python
import os
os.getcwd()
os.chdir('/tmp') ## Only works for Unix... use another dir for windows :P
os.listdir()
walker = os.walk(os.curdir) # returns a generator that traverses the fs tree starting on the argument.
type(walker)
list(walker)
```

A variety of methods allow you to examine, modify, and create or remove directories


```python
f= open('file.txt','w') ## you remember this right?
f.close()
os.stat('file.txt')
os.mkdir('new_dir')
os.rename('file.txt', 'newdir\\file.txt')
```

The os.path submodule provides additional functionality for your path needs.


```python
sample_path = os.path.join('meh','weh','hello')
sample_path
os.path.split(sample_path)
os.path.exists(sample_path)

```

### shutil Module:
living on top of the os module it makes high level operations on files and collections of files easier


```python
import shutil

shutil.copyfile(source,dest) #overwrites dest

shutil.copy(source,dest) #like a cp, if dest is a directory

shutil.rmtree(path) #Must be a real directory

shutil.move(source,dest) # works with directories

```

## RESTful API
How to interact with the outside world, via HTTPS using APIs

For this part of this tutorial, we will be using the requests module. It might already come installed (At least in Anaconda it does )

Otherwise in your terminal you type:

    pip install requests # Or pip3 if you have both python 2 and 3 in the system.

REST is simply a convention for structing a web API.

This means an API that you interact with over HTTP/HTTPS, making requests to specific URLs to obtain information from the destination... or even add information to said destination.

#### These are the kind of request you can do via HTTPS:
    - GET: retrieve information (like search results). This is the most common type of request. The info you get depends on what the API can share.
    - POST: adds new data to the server.
    - PUT: changes existing information. For example, it would be possible to change the value of an existing item.
    - DELETE: deletes existing information,

The information you will request to get/put will usually come in the JSON format (or whatever is your favourite semi-structured and the API supports). That being said, your response could simply be a blob of text. Here is an example:

{
    "id": "your_item",
    "summary": "some info"
}




### Example1:
A GET task


```python
import requests

request_1 = requests.get('https://www.python.org')
request_1.status_code ### to see how this ended a 2xx code usually means success!

if request_1.status_code != 200:
    raise ApiError('GET ended in {}'.format(resp.status_code))
#print(request_1.content) ## You will get a very chunky blob of text!
request_1.headers.get('content-type') # As you can see here it’s no json

#Now let’s try getting the info from a site whose API will return a JSON

request_2 = requests.get('https://httpbin.org/get')
request_2.status_code
request_2.headers.get('content-type') # Now it’s a Json
print(request_2.text)

```

    {
      "args": {},
      "headers": {
        "Accept": "*/*",
        "Accept-Encoding": "gzip, deflate",
        "Host": "httpbin.org",
        "User-Agent": "python-requests/2.22.0",
        "X-Amzn-Trace-Id": "Root=1-5e7cdc22-750e3aea9e903e5e64688542"
      },
      "origin": "46.25.209.181",
      "url": "https://httpbin.org/get"
    }



### Example2:
A POST task


```python
payload = dict(key1='value1', key2='value2', key3='pepe') # what you wish to insert.
request_3 = requests.post('https://httpbin.org/post', data=payload)
request_3.headers.get('content-type')
print(request_3.text) ### look inside the "form" label
```

    {
      "args": {},
      "data": "",
      "files": {},
      "form": {
        "key1": "value1",
        "key2": "value2",
        "key3": "pepe"
      },
      "headers": {
        "Accept": "*/*",
        "Accept-Encoding": "gzip, deflate",
        "Content-Length": "33",
        "Content-Type": "application/x-www-form-urlencoded",
        "Host": "httpbin.org",
        "User-Agent": "python-requests/2.22.0",
        "X-Amzn-Trace-Id": "Root=1-5e7cdc7a-bb72496c709a3610b0e3a830"
      },
      "json": null,
      "origin": "46.25.209.181",
      "url": "https://httpbin.org/post"
    }



#### FINAL NOTE:
If you need to interact with your OS like executing a command ... That is beyond the scope of this guide... Congratulations, that means you are advanced enough to learn about subprocess (and if it’s too complex for your needs... you might try os.system... but better learn the big bad thing)
