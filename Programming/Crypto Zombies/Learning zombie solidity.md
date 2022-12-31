# The Curriculum
## Lesson 1
https://alligator.io/workflow/command-line-creating-files-directories/

knocking these out 1 by 1

### chapter 3: state variables
![[Pasted image 20220128151453.png]]

this is all you need to assign uint values to different integers
![[Pasted image 20220128151524.png]]

### chapter 4: math
Math in Solidity is pretty straightforward. The following operations are the same as in most programming languages:

-   Addition: `x + y`
-   Subtraction: `x - y`,
-   Multiplication: `x * y`
-   Division: `x / y`
-   Modulus / remainder: `x % y` _(for example, `13 % 5` is `3`, because if you divide 5 into 13, 3 is the remainder)_

make sure our Zombie's DNA is only 16 characters, let's make another `uint` equal to 10^16. That way we can later use the modulus operator `%` to shorten an integer to 16 digits.

1.  Create a `uint` named `dnaModulus`, and set it equal to **10 to the power of `dnaDigits`**.

pragma solidity >=0.5.0 <0.6.0;

contract ZombieFactory {

uint dnaDigits = 16;

uint dnaModulus = 10 ** dnaDigits; //start here
}

### chapter 5: structs
for complex data types, solidity has "structs"
Note that we just introduced a new type, `string`. Strings are used for arbitrary-length UTF-8 data. Ex. `string greeting = "Hello world!"`

struct Person { 
uint age; 
string name; 
}

i thought this would be the right answer for having name as string and uint as dnadigits
![[Pasted image 20220128152219.png]]

big wrong tho, instead keep it just as they listed it:
![[Pasted image 20220128152306.png]]

### chapter 6: arrays
// Array with a fixed length of 2 elements: uint[2] fixedArray; // another fixed Array, can contain 5 strings: string[5] stringArray; // a dynamic Array - has no fixed size, can keep growing: uint[] dynamicArray;

there are fixed arrays and dynamic arrays
- fixed with 5 strings
- dynamic with no fixed size

"So creating a dynamic array of structs like this can be useful for storing structured data in your contract, kind of like a database."

this is how you set up storing public data in the contract so that ppl can read it all

1.  Create a public array of `Zombie` **_structs_**, and name it `zombies`.


![[Pasted image 20220128152735.png]]

### chapter 7: function declarations
What is a reference type you ask?

Well, there are two ways in which you can pass an argument to a Solidity function:

-   By value, which means that the Solidity compiler creates a new copy of the parameter's value and passes it to your function. This allows your function to modify the value without worrying that the value of the initial parameter gets changed.
-   By reference, which means that your function is called with a... reference to the original variable. Thus, if your function changes the value of the variable it receives, the value of the original variable gets changed.

so i want to now take the above code and create a public function named createZombie
and this function will have two parameters: the string for name and dna for uint

![[Pasted image 20220128153849.png]]

here i ended up adding the createZombie function with these string and uint added; made public and always remember to add the new parenthesis after public

### chapter 8: working with structs and arrays
so we  had the Person struct
looked like 
`struct Person {
	uint age;
	string name;
}

Person[] public people;`

but now if we want to add new Persons to this and add to a people array (combo of multiple strings etc) then i would create a line of code that looks like this
![[Pasted image 20220128154944.png]]

1.  Fill in the function body so it creates a new `Zombie`, and adds it to the `zombies` array. The `name` and `dna` for the new Zombie should come from the function arguments.
2.  Let's do it in one line of code to keep things clean.

for this step i got the zombies.push right but instead of dna, name it should be _name, _dna_ instead, which allows for the same rep as the string itself
![[Pasted image 20220128155420.png]]

### chapter 9: private/public functions
so solidity functions are public by default
- anyone can use the contracts function and execute

to make them private do this:
`uint[] numbers;

function _addToArray(uint _number) private {
	numbers.push(_number);
}`
in this example, we're basically just modifying the inital function to now be private
![[Pasted image 20220128160808.png]]

