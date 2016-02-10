In Python 2x, exceptions can be caught using both the comma syntax and the 'as' syntax. For instance, the following two options are valid pre-3x:

```python
    try:
        try_body
    except NameError, e:
        except_body
```


```python
    try:
        try_body
    except NameError as e:
        except_body
```

In Python 3x versions, the comma syntax has been deprecated and only the 'as' syntax is supported. 

### Rationale
Python versions before 2.6 allowed you to catch multiple exception types, with the following syntax: 

> except_clause: 'except' [test [',' test]]

However this leads to ambiguity, for instance, in the following case the IndexError is never caught.

```python
>>> try:
...   l = []
...   l[1]
... except NameError, IndexError:
...   print "Caught Exception"
...
Traceback (most recent call last):
  File "<stdin>", line 3, in <module>
IndexError: list index out of range
```

### Grammar
Pre-3x versions of Python let you assign an exception to a variable using the following grammar:

> except_clause: 'except' [test [',' test]]

3x+ versions follow the following grammar:

> except_clause: 'except' [test ['as' NAME]]

### References

[PEP-3110](https://www.python.org/dev/peps/pep-3110/)
