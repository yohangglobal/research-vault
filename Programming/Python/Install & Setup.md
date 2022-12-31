# Installing Python
#Python #dev 

## terminal install
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

## Python 3 & PATH
https://www.youtube.com/watch?v=Ac3w0PjspWw

good article on what i can use to help understand PATH and the diff versions of python more
https://realpython.com/intro-to-pyenv/

fucking godsend for understanding the different PATHs that i'm using
https://stackoverflow.com/questions/50896496/what-is-the-difference-between-py-and-python-in-the-windows-terminal

so basically always use py for doing python shit, bc python is for the installed version on the computer

`python` is the Python executable of the Python installation which you have selected as a default during the installation. This basically put the path to that version inside the PATH, so that the executable is directly available.

`py` is the _Python launcher_ which is a utility that comes with Python installations on Windows. It gets installed into `C:\Windows\` so it’s available without requiring PATH modifications. The Python launcher detects what Python versions are installed on your machine and is able to automatically delegate to the right version. By default, it will use the latest Python version that is on your machine. So if you have installed 2.7, 3.5 and 3.6, running `py` will launch 3.6. You can also specify a different version by doing e.g. `py -3.5` to lauch 3.5, or `py -2` to launch the latest Python 2 version on your machine.

the main component here being that im got confused with the diff versions available but now its clear that i should only be opening via the python launcher "py"

so basically for example with the pip installer, i would do py -m pip install yfinance?

ugh^^ this aint work fucking hell

anyways you install python 3 on windows, but you should always go to the website and install which is what i thought i did originally???

bro does a great job showing how to install the correct location
basically when launching it'll toss that shit in a random spot (for example)

so its installed and im in my user folder:
he did python3 which pulled up Python 3.9.13 for me and is the 64bit AMD on windows 32

then i did exit() to exit and did "py" which opened up the anaconda launcher on windows 32

to find this initial location i would just type in IDLE to my search bar?
yup that works, did so and then got to see IDLE 3.9 as my version

so from here i went to open up IDLE (also found out that i cant run them at the same time? like having python in terminal and then back in the IDLE shell)

![[Pasted image 20220731213229.png]]
interestingly enough this is the same as the python3 and python pull up, not py launcher

but i can go to file>path browser!

**CRACKS ME UP, VIDEO IS USELESS SINCE MY PATH BROWSER DOESNT WORK**

so from here we more onto next install guide
https://www.infoworld.com/article/3530140/how-to-install-python-the-smart-way.html
they say go for the best composability but fuck allat

i did 64bit systems, not sure if i did zip files or not but i feel like i should just scrap everything and start over lol

classic way is still thru python.org http://python.org/

so from here i shouldnt do any pip installs yet! goal is to keep the base layer "python" and "python3" as clean as possible

basically they're saying that i should install python virtual environments first, then install packages there...

so into the "py" python launcher?

## python installer
so this can either be in the program files directory, in my appdata folder under users, or up in a different pythonxy folder

lmaooo im getting so fucking confused, maybe im hurting myself by not just starting fresh...

okay so next step up could just be reinstalling python and getting rid of the other versions bc rn the PATH is what's fucking me up with this shit





## Setting up Anaconda
so first this starts out with the Anaconda thing that is an open source distribution, basically it's largest benefits are that the app is full of features and modules for managing the environments and packages within python

https://www.anaconda.com/products/distribution

so im installing this now and it gave me some options for what to do and add. basically saved in gotchuglobal folder, in applications under anaconda3 for future reference

![[Pasted image 20220731121016.png]]
nice setup frfr! all programs and packages are loaded into anaconda3 and will give me access to the rest of the diff environments that i wish to load!

![[Pasted image 20220731121139.png]]

here i can load these additional IDEs thru dataspell
https://www.jetbrains.com/dataspell/?utm_source=anaconda.com&utm_medium=cpc&utm_campaign=anaconda-installer-2022&utm_term=&utm_content=&=

seems like there's a lot of diff variations of jupyter notebooks that i can acquire and test out, haha this is what it means for something to be open source kek!

this jetbrains one is mostly focused on high interactivity bw command and editor modes, providing smart coding assistance and creating specific consoles and scripts for multiple use cases, such as scientific scripts or data visualization outputs

### anaconda nucleus
there's also the nucleus account from anaconda that offers training materials, how to videos and exactly what's needed for setting up the program

register for an account here:
https://anaconda.cloud/getting-started-with-anaconda-distribution?source=win_installer

https://www.anaconda.com/products/distribution/installation-success

### navigator
so took me just a lil while longer than expected to get it up and running but had to search for navigator app then wait for UI to load up

whole time the conda.exe and other apps are like running no and off kek

## pandas library
and from here i can go right into the anaconda navigator! this acts like a UI for managing all the different packages i'll be using

the first package described is pandas which is a library for manipulating data
1. Click Environments and click base 
2. Select All from the dropdown 
3. Click Update index 
4. Type pandas in the search 
5. Tick the box 
6. Click Apply in the lower-right Now, we need stock price data. For that, we'll install yfinance.

![[Pasted image 20220731122458.png]]

looks like i already have that downloaded! but basically would hit a good ol download to run

i also just adde jupyter notebook and apply, not sure if that works but looking to open up a simple terminal for this

finally figured out that to install this package using pip i can simply do python -m pip install yfinance!
wait can i do the same with pandas?

## pip package installer
so up next is downloading pip which is a python package manager, very important for what ima be using to add stock data. this will be using yfinance to pull data

ran into some issues loading up the package manager, basically that i wm not sure if im in the right area or not
https://packaging.python.org/en/latest/tutorials/installing-packages/

this article describes how to install diff packages correctly, basically that these need to have the right dependencies set up, andddd i need to be running in the right environment!

ofc run py --version first and make sure you have an updated environment.
these commands are supposed to be run in a shell, which im now finding out is a terminal or console as well

it also says to use {sys.executable} to get this installed correctly

Additionally, you’ll need to make sure you have [pip](https://packaging.python.org/en/latest/key_projects/#pip) available. You can check this by running:

Unix/macOSWindows

py -m pip --version

If you installed Python from source, with an installer from [python.org](https://www.python.org/), or via [Homebrew](https://brew.sh/) you should already have pip. If you’re on Linux and installed using your OS package manager, you may have to install pip separately, see [Installing pip/setuptools/wheel with Linux Package Managers](https://packaging.python.org/en/latest/guides/installing-using-linux-tools/).

If `pip` isn’t already installed, then first try to bootstrap it from the standard library:

Unix/macOSWindows

py -m ensurepip --default-pip

If that still doesn’t allow you to run `python -m pip`:
current issues im running into are just items that in the right area? some tools not working either

i got this error as well
https://stackoverflow.com/questions/66322049/could-not-install-packages-due-to-an-oserror-winerror-2-no-such-file-or-direc

https://packaging.python.org/en/latest/guides/installing-stand-alone-command-line-tools/
this is an interesting setup, now i should also look into pipx as well

basically found out that the PATH i was loading on wasnt the right one
so with this i install pipx with py -m pip install --user pipx

okay finally checked if pip was even installed and we can see that this works fine for seeing if this committment is satisfied

py -m ensurepip --default-pip
![[Pasted image 20220731151612.png]]

so this confirms that requirements are satisifed, and shows that py -m is what i should use to launch these tools

okay so now had tried to update the mf package, aint work bc of this error kek

ERROR: Could not install packages due to an OSError: [WinError 5] Access is denied: 'c:\\python39\\lib\\site-packages\\pip-21.1.3.dist-info\\entry_points.txt'Consider using the `--user` option or check the permissions.
![[Pasted image 20220731175423.png]]

https://stackoverflow.com/questions/33608649/python-pip-install-not-working-on-windows
for installing yfinance i basically went thru this page and did python -m pip install yfinance

so change of pace, i can go directly to my user terminal from powershell or command prompt, then type in "py" and pull up the python environment thru anaconda!



## jupyter notebook
pretty interesting i had no idea that this is what this was used for! so its all open sourced and made thru the web itself. pretty damn cool that i can just open up jupyter tests and get to typing!!!
http://localhost:8888/notebooks/Code/jupyter-tests.ipynb

Click home in the Anaconda Navigator, find the Jupyter Notebook app, and click Launch. Enter the code in a cell, and press the Run button to run it. Here's how to get 10 years of price data in 1 line of code:

so now i can just pull up a whole bunch of data from stocks using yfinance??
![[Pasted image 20220731184122.png]]

this is a pretty dope little setup right here!
![[Pasted image 20220731184447.png]]

so first command i can try out is run the data

import yfinance as yf`

data = yf.download("ge", start="2020-01-01", end="2022-07-29")

data

okay so this was the first error that i got, basically saying that no module can be found

ModuleNotFoundError                       Traceback (most recent call last)
Input In [1], in <cell line: 1>()
----> 1 import yfinance as yf

ModuleNotFoundError: No module named 'yfinance'

this looks like it'll initially help ig
https://stackoverflow.com/questions/43872617/numpy-pandas-modulenotfounderror-in-jupyter-notebook-python-3



# pyquant quant and data analysis
https://pyquantnews.com/the-pyquant-newsletter/
https://pyquantnews.com/pqn-001-how-to-45x-python-performance-with-c/


# practical tutorials
this displays a pretty good list of guides and cheatsheets that we can check out
https://github.com/practical-tutorials/project-based-learning#python