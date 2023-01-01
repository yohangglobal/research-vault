# Full Python Course - datacamp
#dev #Python 

https://www.youtube.com/watch?v=rfscVS0vtbw

## Install and Setup
first step is downloading python and then going into the diff versions.
python 3 is the main version i want to go after

use an IDE to apply as a text editor for python
best one is pycharm

downloaded pycharm, now opening up!

![](Pasted%20image%2020220823112040.png)

so for future reference this program is saved in : C:\Program Files\JetBrains\PyCharm Community Edition 2022.2.1

could put in applications but feel like i shouldnt mess with this LOL

now looking at shortcut and PATH variable, not sure what to look for here kek

this answers .py create associations part
https://www.quora.com/Should-I-choose-the-create-associations-py-option-before-installing-PyCharm

so if i only have pycharm as my IDE this is preferred!

update context menu is for when i right click on files and choose to open a file in pycharm
https://www.reddit.com/r/learnprogramming/comments/a0ep5q/pycharm_installation_configuration_options/

installed this into jetbrains as default pycharm place
hmm might take the shortcut of desktop tho, just pin it maybe

almost wrecked tab tho LOL

OKAY INSTALLED BABY

### quick pycharm tour
whoa starts off with a virtual environment? damn so i have a learning project now say less
...hm should i have saved this in Code folder???

hahahah laptop going mad slow rn, only have brave obsidian and pycharm running to!
yeah so this is pulling it up in yan22 appdata, dont want that so i should save in Code instead

now moved to "Code" and also created a PycharmProjects folder as well! maybe i should change Jetbrains to Pycharm?

ight now have this open in the users/yan22/code/pycharm/pycharmprojects folder
![](Pasted%20image%2020220823115023.png)

make sure i have the right interpreter, all good for me since only one was available

### first python program
do New and Python File
now its called app.py saved in pycharmprojects

first up is hello world!!!
inside here im doing the same ol print() function to get a quote from the computer

how do i run this file?
to run this, go to top and hit run

so to run this i should do Run but the second run not the main.py folder
![](Pasted%20image%2020220823115528.png)
BOOM

## Drawing a shape???
so basically whenever i type in a text editor like this, its executing this code in python. point is im giving a computer instructions to use

time to draw a triangle?? 

type: print("") and copy multiple times
he's doing multiple / and creating a triangle to make his own shape! haha not even like a new thing literally just creating the shape himself.

doesnt matter what it is as long as i have print("") i can type whatever
![](Pasted%20image%2020220823134148.png)

so this is what i have so far!

explains console is where python outputs information
goes from the editor -> console to print statements

hahaha nice it worked!!!

![](Pasted%20image%2020220823134257.png)
take note, this pulls up my file as code-pycharm-pycharmprojects-app.py

i can do all of this pretty simply! when this clicks play button it completes this line by line, one step at a time. lil lines and tests are going to help out a lot as i go thru the course. DAMN THIS GUY IS GOATED

## Variables and Data types
so primary focus here is that im going to be using a lot of data when interacting with python! this doesnt matter too much now, but when i start diving into just like data analysis for crypto pairs, i'll be taking in a shit ton of info

coming back 8/27!

so when i take breaks from this i should go back and run similar programs to get back in the game

Variable: a container where we can store data values
makes it easier to work with and manager all in the program

simple program can be i did this, and this happened, but i wanted to change something in the program

imagine this was an entire bio or sum, but you needed it to be changed quickly and easily

![](Pasted%20image%2020220827173004.png)

to add variables you would go above the print statements, then assign a name where info will be held

character_name - separate different names with an underscore
basically saying hey this is the variable and this is its purpose

mine would look like character_name = "bih"
character_trait = bussing

for mine, will be name and trait

i want to put variable in the print statement:
wrap the first part with its own quotes, then the next set of words in its own quotes

![](Pasted%20image%2020220827173527.png)

NICE still worked and now i can edit to make sure the spaces should up correctly but adding one space before end quotes

cool thing: when they want to change shit, just change the variables themselves! will auto update thru the whole story

to change within code itself, just add more lines and assign a diff name
![](Pasted%20image%2020220827173903.png)

Strings: plain text within parts of your code
you can store this shit, all basic text in strings
can also store numbers

i can use whole numbers and decimals as well
store boolean values

boolean: true or false value
this will be important for true and false data

capital True and capital False for this

### concatenate str "int" error
concatenate means linking things together

got first error for this section, trying to add in an integer to my string wont work initially?
https://itsmycode.com/typeerror-can-only-concatenate-str-not-int-to-str/

very simple fix for this was just making the integer a string!

```python
product = {
	"item": "iPhone",
	"price": 1599,
	"qty_available": 40
}

print("We have total " + str(product["qty_available"]) + " quantities of Product " + product["item"])
```

**Output**

```python
We have total 40 quantities of Product iPhone
```

in my case, this was for turning the character_age as 24 in the story

character_name = "bih"  
character_trait = "bussing"  
print("i had that " + character_name + " bussing")  
print("but then she said she tide")  
print("so i said bih you crazy")  
print("get back to working dat neck!")  
  
character_name = "teetee"  
character_age = "24"  
print("ooowee why " + character_name + " think she can get away with this ")  
print("can you believe that she is actually no older than " + character_age + " seriously!")

### true/false values
lots of diff types of data, 99% of time, we got strings, integers, variables, and boolean digits

## Working with Strings
plain text we can put inside of our program -> this is full intro into strings and options

starting fresh and will begin with print("dalkdsfjad sldfkj") for example

haha bet now i know new lines are going to be with \n in the code itself
![](Pasted%20image%2020220827175333.png)

there we go!!!

alternative is doing \" this is the escpae character
this will print out quotation mark instead of everything else

print("hahaha and then she said \"fuck you buddy!\"")
this checks out as the above^

just put the \"" and it should be smooth for including quotation marks

run it back 8/28

another alternative is that i can have this set as phrase = GG Capital
and then combine strings together to bring up our motto

character_name = "bih"  
character_trait = "bussing"  
print("i had that " + character_name + " bussing")  
print("but then she said she tide")  
print("so i said bih you crazy")  
print("get back to working dat neck!\n")  
  
character_name = "teetee"  
character_age = "24"  
print("ooowee why " + character_name + " think she can get away with this ")  
print("can you believe that she is actually no older than " + character_age + " seriously!")  
print("i pulled up on the homies and told em how it was")  
print("hahaha and then she said \"fuck you buddy!\""

**concatenation: adding this shit onto another thing**

**Functions**: things we can do with these diff variables

convert the string into lowercase

company = "GG Capital"  
print(company.upper())

just putting the "." there opens up a lot of opportunities

yeah so tested out the False answer and different phrase to describe if the phrase is all in upper case

company = "GG Capital"  
print(company.upper().isupper())

so for this i can combine each of these to make sure that my string is True. the above converts GG Capital into GG CAPITAL and then confirms that it's upper case

**Length function**: allows for finding the lengths of your string

print(len(phrase))

this pulls up 10, counts spaces as well

an additional one is specifying characters within a string

print(company[1]) this is the second letter of GG Capital

Pulls up G!

Indexes on a string we start with zeroes, this is consistent in all strings so position zero is first character in the string

**Index function**

this will tell you where something is within our string

print(company.index("G"))

index and the string gives me a 0 since its the first part in the string

"ap" in this example starts with the 4th character

**Replace function**

print(company.replace("Capital", "Research"))

very clean way to replace

tested out some different replace functions
![](Pasted%20image%2020220828093511.png)

company = "GG Capital makes the world of crypto research easy to understand."  
print(company + " A place where enthusiasts and newcomers can thrive!")  
print(company.replace("Capital", "Research"))  
  
print(company.replace("makes the world of crypto research easy to understand", "obviously is a great resource for teams and companies to learn from"))

these are basic ways that i can test out functions to try
gotta get comfortable with the strings!

## Working with numbers in python!

basics of using numbers and diff types of numbers

first thing we can do is just print out a simple number
print(2)

this prints out 2, easy peasy

can also do calculations here very simply

print(2.3242 * 32 + 33)

this prints out 107.3744

i can split it up with parentheses as well

% this is read as "mod"?

10 / 3, with remainder of 1

9 and 1, this can come in handy with integers

i can add phrases and variables in this as well

my_num = 24
print(str(my_num))

i have to make sure that the string is there for printing out integers, they dont mix

**absolute value**
in here i can go print(abs(my_num))

this will pull up what real number is

**pow function**
this takes strings to specific powers

print(pow)

**max/min function**
print(max(4, 3, 55))

print(round(3.7))
this is for rounding numbers

### Importing

i would hit from math import * to pull in the math module, these are imported access for math functions

now i can use floor and ceil example for bringing the bottom or top number in a decimal
print(sqrt(64)) for the square root of 64
spits out 8.0

## Getting input from users
https://youtu.be/rfscVS0vtbw?t=2918 at this point

still looking at how to import different modules, got to test this out myself using good ol folio projects! now will continue with this as an easy method for testing out new features that i learn, esp when considering just how many diff functions i still need to learn

