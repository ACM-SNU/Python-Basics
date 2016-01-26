#ACM Hack-It
##Python 3.X
### 1.	Function definition
Functions are present in pretty much every programming language.
They allow you to manipulate and use a piece of code over and over, without typing it repeatedly.
Functions in general comprise of three elements:
1.	Input
2.	Processing the input
3.	Output
A function that sums two values, could take in two values ```a``` and ```b``` as input, then return the sum of these two as ```a+b```.  
To explain functions, I’ll show an example of a function in python, then indicate the key elements.  
``` python
def average(a,b,c):  
    "Averages a,b, and c and returns the mean"  
    ans = (a+b+c)/3  
    return ans  
```
Points to note:
1. ```def``` keyword – tells Python that we are going to define a function 
2. The function name – in this case, average  
3. The arguments of the function – in this case, ```a, b, and c``` : normally, these are supplied in the same order as defined in the function; a function may also have no arguments necessary
4. Documentation – tells the use what the function does (this is optional)
5. ```return``` keyword – tells Python that the function body ends there, and outputs whatever follows it; the return keyword also ends the function call 

In this case, ```average``` takes in three numbers as an input, averages them, then the ```return``` statement outputs the resultant value.  
Unlike in other languages, as we saw earlier, we don’t necessarily have to mention the data type of variables that we use, etc. Here, there is no need to specify what type of data the function takes in those three variables, but clearly they are numbers, since I am doing arithmetic operations on them. If we were to pass any other data type such as a string through, the function call would return an error on the line where the value of ans was being calculated.  

### 2.Function arguments
Function arguments are the parameters given as input to a function. There are different types of arguments. We will cover essential, default and keyword arguments.
#### Essential arguments
Consider a function which adds two numbers. If either of those arguments is not present, then it cannot do anything, and will return an error. Therefore a function such as our average function defined above will always require three inputs.
#### Default arguments
Now consider the following function: 
``` python
def f(a,b=0):
    return a+b
```

If the user fails to supply the value of b, then Python will default it to zero, and the function call proceeds as normal. No errors will be raised. This can be applied for other data types too; for example you could specify an argument called type in the function definition as type= “default”, and Python would set the value to default if no user input was given.  
Also note how an expression was evaluated directly on the return line. Yes, you can do that.
#### Keyword Arguments
If you know the name of the argument then you can write that while calling the function; this allows you to use place arguments in the wrong order and still let the function work. Consider the following bit of code:  
``` python
def order(a,b):
    return a 
>>> order(5,6)  
5  
>>> order(b=6,a=5)  
5  
```
As you can see, when a was specified as 5, the function understood and returned the correct value.  
The next thing to talk about is how arguments in Python are passed. In Python, what you are passing is actually a reference to an object. What you have inside your function is in fact an object. If that object is mutable, then you are free to do so. If not, then you will be unable to. Take for instance an integer. In Python, integers are an immutable data type. So when we pass an integer to a function, and attempt to change it inside, it won’t. See the following example to understand.
  
``` python
a = 10  
def f(a):  
    a=a*a  
    return(a)  
>>> f(a)  
100  
>>> print(a)   
10
```
What if we passed a mutable object? Such as a list? Then see the following example.
``` python
def foo(bar):  
    bar.append("WHATS UP PEOPLE")  
    return  

>>> shopping = ["eggs","milk","bananas"]  
>>> print(shopping)  
['eggs', 'milk', 'bananas']  
>>> foo(shopping)  
>>> print(shopping)  
['eggs', 'milk', 'bananas', 'WHATS UP PEOPLE']  
   
```
Objects like lists, as above, can be changed in that manner.  
Now what if you don’t want this to happen? Well, you could write the following:  
``` python
def foo(bar):  
    bar=["lol"]  
    return  

>>> a=[1,2,3]  
>>> foo(a)  
>>> a  
[1, 2, 3]  
```
In this case what’s happening is that the function is creating a new copy of bar and manipulating that. The original list doesn’t get affected. In order to understand this better, we’re now going to talk about something called *scope*. 

### 3. Scope of variables
Not all variables in a program can be accessed anywhere else. Certain variables will only ‘exist’ or be accessible in some parts of a program – these parts are called their scope. There are two basic types:
#### Global scope
These are generally variables that are defined in the main body of the program; they are not defined inside functions. These can be accessed pretty much anywhere else in the program.
#### Local scope
Variables that are defined inside a function body, for example, are said to have a local scope. They can only be accessed from within the function, and trying to use them from outside the function returns errors. Consider the following example:
``` python
def raj():  
    var = "local variable"  
    print(var)  
    return  
  
>>> raj()  
local variable  
>>> print(var)  
Traceback (most recent call last):  
File "<pyshell#6>", line 1, in <module>  
    print(var)  
NameError: name 'var' is not defined  
```

As you can see it returns ‘var’ is not defined when we try to just type print(var). This is because the variable var only exists within the scope of the function, and nowhere else.
One way to circumvent such an issue is the use of another keyword, called *global*.

``` python
def rohan():  
    global var  
    var = "global variable"  
    print(var)  	
    return  
 
>>> rohan()  
global variable  
>>> print(var)  
global variable
>>>
```
Since we explicitly told Python to allow var to be a global variable, it will now not have a problem when we try to access it from outside the function.  



