# Function Scope and Return Behavior in Python

```{admonition} Overview
:class: overview

Questions:
- How does Python handle variables inside and outside functions?
- What happens when a function doesn't explicitly return a value?
- How can variable naming cause bugs?

Objectives:
- Understand function scope and variable resolution in Python.
- Recognize the importance of `return` statements.
- Avoid common mistakes related to variable naming and scope.
```

## Motivation – Understanding Functions and Scope

Python functions are fundamental for organizing and reusing code. But misunderstanding how variables behave inside and outside functions can lead to confusing bugs. This lesson demonstrates function scope, global/local variable resolution, and the importance of `return` statements.

---

## A Simple Function: `add_two`

Let’s look at a basic function. Before running the code below, take a moment to think:

What do you expect the function to do? Will the last line succeed or raise an error?

```python
def add_two(num1, num2):
    print(f"The value of num1 is {num1}")
    print(f"The value of num2 is {num2}")
    my_sum = num1 + num2
    print(f"The sum is {my_sum}")

add_two(9, 3)
print(my_sum)
```

If we execute the code above, we will see the following:

```
The value of num1 is 9
The value of num2 is 3
The sum is 12
NameError: name 'my_sum' is not defined
```

Calling `add_two(9, 3)` prints the values and their sum. But attempting to access `my_sum` **outside** the function raises an error, because it is only defined within the function scope.

This illustrates an important point: variables created inside a function—known as **local variables**—do not exist outside that function. If you try to access them after the function finishes running, Python will raise a `NameError` because the name is no longer defined.

---

## Local vs. Global Variables: A Subtle Bug

Now let's look at a more subtle case. Try to predict:

What should the sum be? Will this code print what you expect? What variable is actually being used in the calculation?

```python
num_3 = 4

def add_three(num1, num2, num3):
    my_sum = num1 + num2 + num_3
    print(f"The sum is {my_sum}")

add_three(1, 2, 3)
```

If we execute the code above, we will see the following:

```
The sum is 7
```

It might seem like the function should add `1 + 2 + 3`, but the result is `7`. Why?

Inside the function, even though `num3` was passed in as a parameter, the function doesn't use it. Instead, it refers to `num_3`, which is defined outside the function. Python uses the global `num_3` because that is the name it finds in the enclosing scope. This can be easy to miss and leads to results that are technically correct Python but logically incorrect for your intentions.

Careful naming and attention to variable scope can help avoid this kind of mistake.

---

## Clarifying Scope

This next example demonstrates how the same variable name can refer to completely different values, depending on scope.

```python
num3 = 4
print(f"Outside function: num3 = {num3}")

def add_three(num1, num2, num3):
    print(f"Inside function: num3 = {num3}")
    my_sum = num1 + num2 + num3
    print(f"The sum is {my_sum}")

add_three(2, 3, 3)
print(f"Outside function again: num3 = {num3}")
```

If we execute the code above, we will see the following:

```
Outside function: num3 = 4
Inside function: num3 = 3
The sum is 8
Outside function again: num3 = 4
```

Even though the global and parameter variables have the same name, they are completely separate. The `num3` defined outside the function keeps its value of 4 and is unaffected by the function call. This illustrates that **function parameters shadow global variables** with the same name, but do not modify them.

---

## `print` vs `return`

Think about the difference between printing and returning:

What do you think the value of `number` will be? Why might it not be the actual sum? How would you fix it?

```python
def add_three(num1, num2, num3):
    my_sum = num1 + num2 + num3
    print(f"The sum is {my_sum}")

number = add_three(2, 3, 5)
print(f"number = {number}")
```

If we execute the code above, we will see the following:

```
The sum is 10
number = None
```

Even though the function prints the sum, it does **not** return anything. In Python, functions return `None` by default if there is no `return` statement. So even though we saw `10` printed, `number` is assigned the value `None`.

To fix this, we need to add a `return` statement:

```python
def add_three(num1, num2, num3):
    my_sum = num1 + num2 + num3
    return my_sum

number = add_three(2, 3, 5)
print(f"number = {number}")
```

If we execute the code above, we will see the following:

```
number = 10
```

Now `number` is assigned the value returned by the function.

---

## Jupyter Notebook Behavior

Let’s look at how this behaves in a Jupyter notebook:

```python
add_three(2, 3, 5)  # Will show return value if it's the last line
```

If we execute the code above in a Jupyter notebook, we will see:

```
10
```

That’s because Jupyter cells automatically display the value of the last line if it's not assigned to a variable.

Compare that to this version:

```python
number = add_three(2, 3, 5)  # Won’t display anything unless you print it
print(number)
```

If we execute this version, we will see:

```
10
```

Here, the result is only shown because we explicitly used `print`. Assigning a value to a variable suppresses automatic display.

---

```{admonition} Key Points
:class: key

- Variables created inside a function are not visible outside it.
- If you accidentally use a global variable, Python may not warn you.
- Always use `return` when you want a function to output a value.
- In Jupyter, return values show automatically if not assigned.
```
