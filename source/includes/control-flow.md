---
title: Control flow
---

# Control flow

Consider your code as a map. The machine is like a laser sharp _pointer_ focused o a single line of your script (the backend). Each line has a corresponding output and each action (`input()`) has a corresponding reaction. Control flow directs where the _pointer_ moves.


## Conditional statements

```python
propert_price = int(input("What is the price of your property: "))

if property <= 1000:
    return "Let's make this deal happen."
elif property <= 1200:
    return "Let's talk this out."
else:
    return "Call me back in 1 year."                    # good practice to prepare a condition for edge cases

if property <= 1000:
    return "Let's make this deal happen."
else:
    if property <= 1200:                                # see the nested condition
        return "Let's talk this out."
    else:
        return "Call me back in 1 year."
```
Conditional statements act like switches to direct the _pointer_ down one of many paths

All `if` conditional statements are boolean values. Thus, more complex flows are just simple conditions nested together. The 2 code examples are equivalent.

It is good coding practice to keep nested code blocks to a minimum. When possible, follow the first example that uses `if, elif,else`.

- Checking if variable exists
If you are check if a value exist, use the `if variable:` condition. This uses the [truthy](#) logic.

- Return statements
Take note if you are using return statements. Each function call will only execute one return statement. Ensure that your conditional statement does not contain 2< or no return statements.
<aside class="notice">
    Return is only used for function calls. Ensure that your code is within a function block, else it will cause an error.
</aside>
## Loops

```
for word in sentence:
    print()
```

An iterator/iterable is an object that reads one value/element at a time. For example, sequence types (strings, list, tuples) or non-sequence containers (dictionary, files).

A `for` loop is a pre-determined number of iterations, where you are aware of how many time the code block will run. A `while` loop is an indefinite iteration, where the number of loops is unknown and only ends when the condition is met.

A good naming convention is to use singular-plural dyads:
`for word in sentence: `

### Range()

```
for i in range(1, 100, 2):
    print(i)
```

Loops work well on pre-determind, fixed iterables. Create a loop with `range()`. This is an immutable sequence of integers. The arguments are (start, stop, step).

### Break and continue flow

```python
manifest = [("bananas", 15), ("mattresses", 24), ("dog kennels", 42), ("machine", 120), ("cheeses", 5)]

weight = 0
items = []
for cargo_name, cargo_weight in manifest:                               # call both elements in the tuple
    # current weight after the previous loop
    if weight >= 100:
        print("  breaking from the loop now!")
        break                                                           # stop the loop immediately.
    elif weight + cargo_weight > 100:                                   # check in advance
        # skipping this iteration of (cargo_name, cargo_weight)
        continue
    else:
        items.append(cargo_name)
        weight = weight + cargo_weight

print("The final weight is {}, holding {} items.".format(weight, items))
```

Within loops, you may customize flows which allow the loops to `break` when a certain condition is met, or skip this iteration and `continue` with the next.

This is useful for loops that iterate over an unknown number of variable (e.g. `while` loops).

