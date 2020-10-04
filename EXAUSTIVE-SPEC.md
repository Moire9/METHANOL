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

The basic subunit of code in PythonScript, as it's a functional language. You can think of it as a special case of the jump

### Declaration

```PythonScript
/!<function label>! [ <args...< >> [
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

Logic in PythonScript is *all* done using ternary logic (& numbers) - "trits" with 3 states (hence the base-3 number system).

### Equality

```PythonScript
/== <left> <right> \\ returns true if <left> == <right>
```

### Inequality

[FIXME]: # (Might need to change based off how NOT is implemented)

```PythonScript
/!= <left> <right> \\ !(<left> == <right>) 
```

**//TODO:** Remaining operators

[//]: https://hackaday.io/project/164907-ternary-computing-menagerie/log/162816-tritwise-operations-and-eating-crow (This might be a good reference)

## Control Flow

### if

if is just a function an evaluates a condition and executes a code block if it's true. You can define similar functions yourself 

```PythonScript
/if <condition> [
*<conditional statement if conditional is 2>*
;; [
*<conditional statement if conditional is 1>*
;;
```

#### logical extension: named conditionals

```PythonScript
/=!myIf! [ if <condition> [
*<conditional statement if conditional is 2>*
;; [
*<conditional statement if conditional is 1>*
;;
;myif;
```

### else

```PythonScript
/else <if conditional (named or otherwise)> [
*<conditional statement if conditional is 0>*
;;
```

## labels

labels for parts of your program (to be used with jumps)

```PythonScript
/!<label name>
```

## jump

Loops are for the weak. In PythonScript all looping is done with jump statements.

```PythonScript
!<destination label>
```
