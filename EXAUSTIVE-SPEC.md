# Complete Spec Organized By Operation

Values inside `<>` indicate values the user can manipulate as well as notation used by this spec. This was chosen due to the heavy overloading of square brackets.

`<identifier>...<<separator>>` indicates a variadic number of a parameter identified by `<identifier>` separated by the value in `<separator>`

`<||>` OR

`<if <condition>>` if `<condition>`

`*<purpose>*` indicates a region in which any instructions may be given

## Code Blocks

The basic scoping unit of PythonScript, opened with `[` and closed with `;;`

```PythonScript
[ *<inner code>* ;;
```

## Functions

The basic subunit of code in PythonScript, as it's a functional language.

### Declaration

```PythonScript
/=!<function name>! [ <parameters...< >> [
*<inner code>*
;<function name>; <||> <if> <at top level> ;;
```

### Calling
