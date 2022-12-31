# Python Tutorial from W3Schools
#dev #courses #Python 

## Python Intro

So Python is a very popular programming language, i think i first heard about it like maybe college? but not even that much tbh, prolly didnt become familiar until post college that it was this huge benefit to data analysis

now i found out it was released in 1991 and is used for web dev, sw dev, math and system scripting

### benefits
server for creating web apps
i can improve workflows and handle big data

syntax is great for new beginners and has easier functionality for the avg user

### hello world
print("Hello, World!") good ol classic command for getting a phrase to be typed out thru compouter is this!
![[Pasted image 20220614214215.png]]

the quickstart part would have to be in the command line
i can do python helloworld.py to enter a new file


## Python Install
https://www.w3schools.com/python/python_getstarted.asp

okay so went thru ze usual python --version to check if i still had python (i did)
now finding out that i would write .py files into a text editor -> python interprets the language to display what i made?

oh woww just found out that "dir" is all i need to view all directories in a certain folder thats mad cool
mkdir is the one to make a new directory in my folder!

**basically to launch python all i would do is open up command prompt
type in py**

python 3.9.6 should pop up with >>>

Then i can continue and write test out whatever code there in the command line

for instance with Hello world i would simply

print("Hello Worldddd")

hahaha BAG!!!!
**I can just exit python command line by typing in exit()**

## Python Syntax
### Python Indentation
So we indent the beginning of code lines to assist with readability usually. However with Python scripts we are using this to indicate a block of code

if 5 > 2:  
  print("Five is greater than two!")

One interesting thing i learned here is that its common to see 4 indents, but only need one

so i can do 
if 5 < 2:
	print("Five is greater than two!")

ow holy shit so interestingly enough i went to command prompt, typed in the folder i wanted to create a directory in, which was python-tutorial, did "mkdir" to make a new directory in the folder, then did cd "name of directory" then just did code python-indent to pull up the directory in VS Code!!!

![[Pasted image 20220624203054.png]]

so now from here i see that i can open up these diff things, make new directories, then immediately run em in vs code thru the command prompt!!!!

![[Pasted image 20220625204608.png]]

here i was able to run the 5 greater than 2 line and print out the following result using the terminal in vs code

### Python Variables
so variables are simply whatever we assign a value to

for example x = 5 and y = "Hello, World"
there's no command for declaring a vaariable either

### Comments
simple as making a new title on obsidian
all you do is good ol # This is a comment and everything is a comment

![[Pasted image 20220625210536.png]]
so far i put it all together to create this string where we would emphasize that print can be used for variables as well

## Python Comments
#Python can have comments within the code

print("Ay im walking here!")

i can put this anywhere in the line of code!
"""
now think of it like this, whenever you see me in the streets, holla YA DIGG
"""
print("ay YA DIGG")

okay popping back in after a long while, it's now july 31st and we're currently getting confused by the diff setups. like where tf is python setup, wtf is PATH lolol this is fucking painful!

well anyway i know that doing 
good ol hashtagprint then ("Hello, World")
print("Cheers hello gang")

this is a great headsup as to what i can write in this mf but gahdamn i got so confused by this other shit

so i know that multiline comments are simply a hashtag on each line

or i can just do triple quotes to make that work as well

## Python Variables
so these are containers for storing data values

this is basically whenever i assign values to certain lettering, very similar to what i set up with aliases in the good ol gahdamn ichibot

so for example this would look like 
x = 5
y = "John"
print(x)
print(y)

and then i would get a certain print out of 5 and John

remember to put variables around strings and leave integers as they are. you can switch variables in each command line as well so x isnt always a specific thing

#### Casting
So this refers to specifying the data type of a variable. hm not sure just yet what the benefit is here, esp when considering each setup is different

ohhh okay so if i print x now that 3 will come out as '3'

x=str(3)
y=int(3)
z=float(3)

then print each one gives a different output. very good to know here esp when putting together a lot of variables

#### Get the Type
oh and then if i forget a certain data type i can use the type() function instead

so if i have x=5 and y="john"

i can do print(type(x)) and print(type(y)) to pull up the various types and the actual variable

#### Single/Double
i can declare something as a string with both type of quotes '' makes life much easier

These variable names are also case sensitive tho which i should keep in mind as well

a=4
A='Sally' two different results here

### Variable Names
So continuing with Variables
this next part focuses on assigning short or longer descriptive names to variables

main rules:
- variable name must start with letter or underscore
- cant start with a number
- only contains a-z, 0-9, and __
- these are case-sensitive as well (age Age AGE all diff)

myvar="john"
my_var="yessah"

2myvar, my-var, my var
none will work

#### Multiwords Variable Names
for making these variables easy to read i can change the capitals on each

myVariableName="John"

theres Camel case ^^^
Pascal case: all capitals
Snake case: all underscores

#### Assign multi variables
oh this is nice i can do it all in one line thank god

so now i can set up x, y, z= "Yes", "maybe", "possibly"
and then do print(x+y+z)

spaces remember to add in the quotess themselves

#### One value multi variables
x=y=z="YESSAH"

= for same variable values

#### Unpack collection
shit this is pretty cool, so now i can have a collection of variables
then set that up with diff variables that relate to that collection

ie doing fruits=["apple", 'banana', 'cherry']

x, y, z=fruits

now each variable is one of the fruits, x apple, y banana, z cherry

### Output variables
so this goes over how print will print out a certain variable

x="python cool as shit wtf"
print(x)

>>> print(x)
python cool as shit wtf
>>> print(x,y,z)
python cool as shit wtf banana cherry

same thing as i been doing, can output variables with diff functions, can also do a simple + and combine them all

Notice the space character after `"Python "` and `"is "`, without them the result would be "Pythonisawesome".

cant combine strings and integers with +, instead you have to put commas for that

so if i do x=10 and y='John has ' z='apples'

i would do print(y, x, z)

>>> x=10
>>> y='John has '
>>> z='apples'
>>> print(y,x,z)
John has  10 apples
>>> y='John has'
>>> print(y,x,z)
John has 10 apples

To print both data types i would do print(x, y)

### Global variables
so here this is where i can use global variables both inside and outside of functions

for instance, i set x='awesome'

then have a new function that says
def myfunc() 
	print("Python is " + x)

my func()

here i would do the above string but final output would be with print('Python is ' + x)

Python is cool

If you create a variable with the same name inside a function, this variable will be local, and can only be used inside the function. The global variable with the same name will remain as it was, global and with the original value.

This prints out the new wording of fantastic
for example if i add x = fantastic into the def function

Nice addition here is the global keyword

can do the above 
def myfunc()
	global x
	x = 'fantastic'

This makes x a global variable

## Python Data Types
So all of these types can do different things and have diff functions

Text Type:

`str` ' Hello world'

Numeric Types:

`int` is 5, `float` 20.5, `complex` 1j

Sequence Types:

`list` is with [], `tuple` is with (), `range` is with (int)

Mapping Type:

`dict` is {'name' : 'John', 'age' : 36} this defines John is 36 (must be in the curly bracket)

Set Types:

`set` does {} and same as list, `frozenset` freezes teh set

Boolean Type:

`bool` True or False

Binary Types:

`bytes` is saying b'Hello' not sure why, `bytearray`, `memoryview`

None Type:

`NoneType`

As before I would type out print(type(x)) to get the type of x variable

Each data type can be assigned by simply defining the value of the variable

Interesting part is that List and Tuple print out same things but just in [] vs ()

![](Pasted%20image%2020221006153106.png)



## Python Numbers


# Python.org Tutorial
https://docs.python.org/3/tutorial/appetite.html