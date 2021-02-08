---
title: List comprehension
---

# Working with python list

```
# Bad practice.

count = []
price_list = [1,2,3,4,5]

for i in price_list:
    count = count + i
```

Python lists are wonderful. They perform `.pop`, `.append` at O(1) time, as well as index operations at O(1) - combining the best of the Array and Linked List data structures.

However, python is horrendously slow at performing custom operations to create, edit, or filter lists. Thus, it is recommended to use either a built-in function or to use list comprehensions.

## `zip()`

```
x, y = [1, 2, 3], ["a", "b", "c"]
zipped = zip(x, y)
print(list(zipped))                     # [(1, "a"), (2, "b"), (3, "c")]
x2, y2 = zip(*zipped)
print(x == list(x2) and y == list(y2))  # True
```

You can create ordered data by _stitching_  matching pairs from different data containers.

Use `zip()` to pull together _n_ list into a list of tuples. `zip()` also works to un-zipped a _n_ dimension list.

## `enumerate()`

```
seasons = ['Spring', 'Summer', 'Fall', 'Winter']
print(list(enumerate(seasons)))                     # [(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
```

Use `enumerate()` to create ordered data containers by attaching the index as a __index__:__value__ pair.

## `map()`

```
map(lamda x: print(x), range(10))
```

This is the equivalent of `.each` in Javascript or `.foreach` in Ruby. This is a top-level function.

Supply a function variable and _n_ iterables to apply the function on.

## List comprehension

```
long_method = []
for x in range(0, 9, 2):
    long_method.append(x**2)                                            # [0, 4, 16, 36, 64]

lamba_method = list(map(lambda x: x**2, range(0, 9, 2)))
short_method = [x ** 2 for x in range(0, 9, 2)]                         # list
generators = (x ** 2 for x in range(0, 9, 2))                           # generator
```

List comprehension provides a concise way of creating lists. For more information, see [here](/python/basics/data-types-and-operators/data-container-methods.md#list-methods).

<aside class="success">
    See here for more information on [generators](/iterators-and-generators/iterators-and-generators.md).
</aside>
