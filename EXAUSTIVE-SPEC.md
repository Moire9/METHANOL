# Complete Spec Organized By Operation

Values inside `<>` indicate values the user can manipulate as well as notation used by this spec. This was chosen due to the heavy overloading of square brackets.

`<identifier>...<<separator>>` indicates a variadic number of a parameter identified by `<identifier>` separated by the value in `<separator>`

`<||>` OR

`<if <condition>>` if `<condition>`

`*<purpose>*` indicates a region in which any instructions may be given

## Number System

PythonScript uses a base-3 number system. The symbols 3-9 are evaluated like any other symbols (meaning you can use them as definition names)

```PythonScript
210 \\ == decimal 21
```

## Code Blocks

The basic scoping unit of PythonScript, opened with `[` and closed with `;;`

```PythonScript
[ *<inner code>* ;;
```

## Functions

The basic subunit of code in PythonScript, as it's a functional language.

### Declaration

```PythonScript
/=!<function name>! [ <args...< >> [
*<inner code>*
;<function name>; <||> ;; \\ used to end most recent block
```

### Calling

functions are called using reverse polish notation

```PythonScript
/<function name> <args...< >> ]
```

### Returning Values

A Preceding slash before an execution block indicates that you want to return a value. Using this outside of functions should result in a syntax error.

```PythonScript
//<function call> <args..< >> ]
```

## Assignment

assignment is a special function/operator that allows you to define symbols

```PythonScript
/= <identifier> <value>
```

as you can see, function definitions are just a special case of assignment

## Operators

In PythonScript, all operators are functions, and so are called with the same notation as functions.

### Required Operators

#### Addition

```PythonScript
/+ <left> <right>
```

#### Subtraction

```PythonScript
/- <left> <right>
```

#### Multiplication

```PythonScript
/x <left> <right>
```

#### Division

```PythonScript
/\ <left> <right>
```

#### Exponentiation

[//]: # (TODO: add "variadic" exponentiation operator to spec)

```PythonScript
/xx <left> <right>
```

## Logic



## Tritwise Operators

**TODO**

[//]: https://hackaday.io/project/164907-ternary-computing-menagerie/log/162816-tritwise-operations-and-eating-crow (This might be a good reference)