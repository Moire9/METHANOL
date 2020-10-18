# Complete Spec Organized By Operation

Values inside `<>` indicate values the user can manipulate as well as notation used by this spec. This was chosen due to the heavy overloading of square brackets.

`<identifier>...<<separator>>` indicates a variadic number of a parameter identified by `<identifier>` separated by the value in `<separator>`

`*<purpose>*` indicates a region in which any instructions may be given

## Number System

METHANOL uses a base-3 number system. The symbols 3-9 are evaluated like any other symbols (meaning you can use them as definition names)

**//TODO:** Negative numbers

```METHANOL
210 \\ == decimal 21
```

## Code Blocks

The basic scoping unit of METHANOL, opened with `[` and closed with `;;`

```METHANOL
[ *<inner code>* ;;
```

## Functions

The basic subunit of code in METHANOL, as it's a functional language. You can think of it as a special case of the jump

### Declaration

```METHANOL
/!<function label>! [ <args...< >> [
*<inner code>*
;<function name>; <||> ;; \\ used to end most recent block
```

### Calling

functions are called using reverse polish notation

```METHANOL
/<function name> <args...< >> ]
```

### Returning Values

A Preceding slash before an execution block indicates that you want to return a value. Using this outside of functions should result in a syntax error.

```METHANOL
//<function call> <args..< >> ]
```

## Assignment

assignment is a special function/operator that allows you to define symbols

```METHANOL
/= <identifier> <value>
```

as you can see, function definitions are just a special case of assignment

## Operators

In METHANOL, all operators are functions, and so are called with the same notation as functions.

### Required Operators

#### Addition

```METHANOL
/+ <left> <right>
```

#### Subtraction

```METHANOL
/- <left> <right>
```

#### Multiplication

```METHANOL
/x <left> <right>
```

#### Division

```METHANOL
/\ <left> <right>
```

#### Exponentiation

[//]: # (TODO: add "variadic" exponentiation operator to spec)

```METHANOL
/xx <left> <right>
```

## Logic

Logic in METHANOL is *all* done using ternary logic (& numbers) - "trits" with 3 states (hence the base-3 number system).

### Equality

```METHANOL
/== <left> <right> \\ returns true if <left> == <right>
```

### Inequality

[FIXME]: # (Might need to change based off how NOT is implemented)

```METHANOL
/!= <left> <right> \\ !(<left> == <right>) 
```

**//TODO:** Remaining operators

[//]: https://hackaday.io/project/164907-ternary-computing-menagerie/log/162816-tritwise-operations-and-eating-crow (This might be a good reference)

## Control Flow

### If

if is just a function an evaluates a condition and executes a code block if it's true. You can define similar functions yourself 

```METHANOL
/if <condition> [
*<conditional statement if conditional is +>*
;; [
*<conditional statement if conditional is 0>*
;;
```

#### Logical Extension: Named Conditionals

[//]: # (Not needed?)

```METHANOL
/=!myIf! [ if <condition> [
*<conditional statement if conditional is +>*
;; [
*<conditional statement if conditional is 0>*
;;
;myif;
```

### Else

```METHANOL
/else <if conditional (named or otherwise)> [
*<conditional statement if conditional is ->*
;;
```

### Labels

labels for parts of your program (to be used with jumps)

```METHANOL
/!<label name>
```

### Jump

Loops are for the weak. In METHANOL all looping is done with jump statements.

```METHANOL
!<destination label>
```
