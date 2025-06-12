
## Preface 
`Think Pythonically` is a Python  tutorial, but unlike other tutorials, here the focus is not on the syntax, but how to *think* about code in Python. 

Before starting this tutorial, it would help if you have python installed. However, you can use the python interface on [this website](https://www.w3schools.com/python/trypython.asp?filename=demo_default) that runs python code for you in the browser. Do delete the existing demo text before you begin! 

# Chapter 1: Assigning Variables 
> [!Note: ] 
> This section does not produce any visible outputs. This is to learn how to think about code. 


You can think of variables like boxes. You can store something in a variable, and you can store variables in other variables. It'll make more sense once you look at the code. Variables can be named anything you like. To illustrate this point, I've named mine `bartholomew`: 

```
bartholomew = 5
```

The above line of code assigns the value of `5` to a variable named `bartholomew`. Now, this may sound simple enough at first, but something strange is actually going on behind the screen. Take a look at this code: 
```
x = 5 
y = x 
x = 10 
```
Looking at the above code, what do you think the value of `y` is once you read line 3? If you said `10`, you'd be (understandably) upset to find out that the answer is `5`. 

To a programmer this may feel intuitive, obvious even, but when I first approached programming this confused me. The issue does not lie with our understanding of how variables work, but instead in understanding how the `=` sign works. Here is how you *should* be thinking of any *assignment* statement (think whenever `=` appears): 

> [!Key Tutorial Term: Evaluate ] 
> This means to simplify and process as much as possible. For example, the evaluation of `2+2` would be `4`. 

When you say `some_variable_name = some_value`, what Python does is first look at `some_value` as a mathematical expression to be evaluated. For example, the evaluation of `5+5` would be `10`. Now how about I say "evaluate `5`"? Since you're not doing anything to the `5`, you get the value `5` from evaluating it. 

>[!Key Idea: ] 
>Python evaluates the expression to the right of the `=` and then stores the *result* in the variable, but **does not store the expression itself**. Do note, that during evaluation itself, however, python goes left to right. 
>
>left_hand_side = right_hand_side 
>evaluates the right hand side from left to right! 

Looking back at the code example, let's rewrite it a bit to show what the computer is thinking (lines with `#` are ignored by computer - these are called comments. Think of them like annotations for your code). 

```
x = 5 
# computer evaluates 5 to result in 5 and stores this 5 in x 

y = x 
# computer evaluates x to result in 5 and stores this 5 in y 

x = 10 
# computer evaluates 10 to result in 10 and stores this 10 in x 
```

Notice how the value of `y` does not change, despite it being defined as the value of `x`. This may seem trivial to begin with, but in a few chapters this trivial concept forms the lynchpin of various algorithmic possibilities. 

But just using numbers isn't particularly exciting, so let's expand! 
``` 
# this is a string - a collection of ordered alphanumeric characters 
bartholomew = "hi" 
# computer evaluates "hi" to result in "hi" and stores this in the variable 
```

Surrounding any collection of alphanumeric characters in quotation marks makes them a string, such as "hi", "hello", "or even this text, yes you can store more than one word." 

Quick question! Are `x = 5` and `y = "5"` the same? Since I'm asking, you probably realise that the answer is no. And you'd be right, *5* is an integer, but *"5"* is string - a collection of one character (the character '5'). 

> [!Key Term: Algorithm ]
> An algorithm is a set of steps. For example, "go straight, then take a right, and then the second left" is an algorithm to... I'm not sure where but you get the idea.

# Chapter 2: The `print` statement and some tricky logic 
> [!Note: ] 
> This section produces visible outputs. 

So far we've stored a value in a variable, but if you run the code you'll notice that nothing is outputted. This is because we haven't told python to output anything! 

A simple function to do this is called the 'print' function. But before we get to that, let's take a look at what functions are! 

## How to think about `functions` programmatically 
A function is a machine. You give it some raw materials, it processes them, and then produces a product. The manner in which it processes them is always the same, even if you give it varying raw materials. Like a washing machine, for example! it doesn't matter what clothes you put in it, their colour or size, they are returned in a cleaner state (hopefully) than when you put them in. Notice that the output still depends on the input, even if the steps are the same. **Most importantly**, if you give the same inputs, you *always* get the same output. 

---

In Python, a function is a machine, and the raw materials it takes are called *arguments*. For example, the *print* function takes a *string* and outputs it to the *console* (the giant black space to the right). The writing is identical to mathematical notation. For example, 

In mathematical notation the function `f` defined as 
$$
f(x, y) = x + y 
$$
would mean that 
$$
f(5, 6) = 5 + 6 
$$
which would evaluate to 
$$ f(5, 6) = 11 $$ 

`Python` has the function `sum`. It does the same! For example, in `Python` 
```
sum(5, 6)
``` 
would evaluate to `11`. 

But wait! Run the code above. Nothing is outputted! That's because `python` performs the evaluation, but doesn't know what to do with the result yet. Let's tell it: 

```
bartholomew = sum(5, 6) 
```

This stores the result in the variable! Remember: evaluate the right hand side first! Now that we've stored the value, let's tell `Python` to display it. 

`Python` has a function to do this! That's right, functions aren't limited to maths. The function `print` takes the stuff it has to display as its input: 

```
print(bartholomew)
```

This would evaluate `bartholomew` to `11` and use `11` as the input. For the `print` function, this would be the displaying of the string "hi" in the *console*. Run it and see! 

>[!Note: ] 
>Notice how the variable is evaluated even though there is no `=` sign! The inputs are always evaluated first, and the result is sent to the function process! As such, 
>```
>sum(5+5, 6) 
>``` 
>Would be the same as 
>``` 
>sum(10, 6) # 5+5 is evaluated 
>``` 
>Which would evaluate to 
>```
>16 
> ``` 

> [!Bonus: ] 
> Now try print(5)! Do you get an output? Yes? Strange? After all, didn't I say 5 is an integer, and not a string? Well, the print function automatically converts it to a string! Pretty nifty! 

# Chapter 3: Mathematical Operators 
The last section gave a sneak peak at this, but let's get our heads around it anyways! First off, the basic mathematical operators remain the same: 
### Addition and Subtraction 

```
x = 5 
y = 10 
z = x + y 
print(z) 
# output should be 15 
```

Subtraction is the simple `-` sign, 
```
x = 5 - 5 
print(x) # should output 0 
```

but division is divided into 2 forms! 

## Division 
`//` vs `/` 
Evaluating `x = 11/2` results in `x = 5.5`
Evaluating `x = 11//2` results in `x = 5` 

Caught on yet? When you use `//`, any remainder is ignored. When you use `/`, it is evaluated like normal division. 

But hey! What *is* `5.5`? It's not an integer, since it has a decimal value, but it's not a string either? 

Decimal values are stored in a third form of data, called ***floats***. You can treat them just as you would regular decimal numbers, for now. 

## Multiplication and Powers 
Multiplication uses the conventional `*`, but putting `**` means *raised to the power of.* 
For example `2*5` evaluates to `10` but `2**5` evaluates to `32`. 

> [!Question: ] 
> What do you think happens when a string is added to a string? For example: 
> ``` 
> bartholomew = "hi" + "sup" 
> print(bartholomew) 
> ```
> Answer: The output is "hisup"! Now what about: 
> ```
> bartholomew = "hi" + 5 
> print(bartholomew) 
> ```
> The output is... an error message. Python does not allow you to add different types of data to each other (exceptions exist, such as floats and integers, like in `0.5 + 5`). 

# Chapter 4: Basic Data Structures 
## What are data structures? 
Data structures are ways of/templates for organising your data. Think of a telephone directory; it's a real-world application of a data structure! Data can be added to these in a predictable manner. 

Lists are a simple example in the real world. You can make a list of many things: books you want to read, movies you want to watch, things you need to buy, things you need to do. A telephone directory is another example. 

A data structure is an arrangement of data that fulfills the following criteria: 
1. It can contain multiple bits of data 
2. The system for the arrangement of the data is known (the arrangement can be random, but this has to be *known*) 

## Structures: 
1. Lists 
2. Tuples 
3. Dictionaries 

#### Lists and Tuples: 
These are the easiest to understand. 

A list is an collection of bits of data. In Python, you can create a list like so: 
``` 
list_variable = ["hey!", "this is", "a list of", 5, "elements!" ]
```

The `[` and `]` are used to show the start and stop of lists, with each element of the list distinguished by a `,`. Notice that the list can contain multiple different data types: the list above contains 4 strings, and 1 integer. 

For tuples, simply swap the `[` and `]` with `(` and `)`. What's the difference? Well, for now let's pretend they're the same as lists. The difference will become clear in the next section. 

##### Slicing 
Say you have the list from earlier: 
```
list_variable = ["hey!", "this is", "a list of", 5, "elements!" ]
```

And you want to find out what the 4th element of this list is. In python, you can use something called **slicing**. 

```
fourth_element = list_variable[3] 
``` 

Placing a number is `[` and `]` next to a list results in the element at that position being returned. Here's how python evaluates it: 

```
fourth_element = list_variable[3] 
→ fourth_element = ["hey!", "this is", "a list of", 5, "elements!" ][3] 
→ fourth_element = 5 
```

But wait! Something strange: I said we were gonna get the 4th element, and we did, so why are we using 3? 

This is a tricky concept called **0 base indexing**. Sounds complicated, but it's super easy. In python, instead of numbering elements as: 
```
list_variable = ["hey!", "this is", "a list of", 5, "elements!" ] 
# positions =       1       2          3         4   5 
```
Python instead does: 
```
list_variable = ["hey!", "this is", "a list of", 5, "elements!" ] 
# positions =       0       1          2         3   4 
```
That's right: python counts from 0, not 1. Thus, the 4th element in the list is actually at position 3. 



# Chapter 5: Loops 
To be added 