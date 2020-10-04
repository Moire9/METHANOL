This is an informal specification for PythonScript, a formal one will follow later. 

##Rundown of basic features
PythonScript is loosely based off of Python. PythonScript does not have classes, fields, or namespaces. Example program:
```
\\ Double backslash indicates a comment.

/=!main! [ foo bar [ \\ Declare a new function "main" that accepts two variables, foo and bar. The [ indicates the beginning of variables and / the end. The ! creates a label, don't worry about that right now.

  /print "Hello, World!"]: \\ A slash indicates the beginning of a function execution. A colon indicates the end of an instruction
  \\ Technically / is an operator that takes the function's name as the first argument, and the function's arguements as the following arguments.

;main; \\ The end of a code block is denoted with the block's name or label surrounded by semicolons. Leaving out the label will end the topmost code block.

/main 0 "h"]: \\ Execute the main function, passing parameters 0 and "h".

\\ PythonScript has a few operators. Note that PythonScript uses polish notation for all operators, with a closing bracket to indicate the end of that function.

/print /+ 22 21]]: \\ Add 22 and 21 and print them.

\\ PythonScript's operators are: + for addition, - for subtraction, x for multiplication, and \ for division. You may have noticed that x is used for multiplication.
\\ Being an operator, x cannot be used in identifiers. You will have to find another alternative.

/= eight 1]: \\ Assign 1 to the variable eight

\\ PythonScript supports literal reassignment, making it an extremely flexible language. For example,

/= 12 22]:

\\ You may have also noticed that the assignment operator is also used to create functions.

/print + 2 10]]: \\ This will print 22

\\ I should also mention that PythonScript uses the ternary number & logic systems. Tritwise and logical operators can be applied to all objects with support for them.
\\ Additionally, users can implement their own tritwise operators. Since no distinction is made between operators and functions, making one is quite simple.
\\ Note that PythonScript won't stop you from implementing functions or variables that override keywords (such as / and [ and ]), however doing so is likely a bad idea.

/=!$! [ one two [ \\ declare a function $ that returns the the sum of the two values halved.

	//\ /+ one two] 2]: \\ a preceding slash indicates that the value will be returned from the function. There are two slashes here since it is returning the output of a function.
	\\ Note that in PythonScript since everything is technically a function, order of operations is ignored and evaluated left to right.
;; \\ This has the same effect as ;$;
\\ PythonScript has relatively few restrictions on what things can be named
\\ Because of literal reassignment, you can even have variables or functions with spaces in their names (as long as they are wrapped with quotes)


\\ Let's talk about control flow. Code blocks start with a [ and end with a ;[block name];

/if 1 [ \\ if is just a function that takes two arguments, a boolean expression and a code block. optionally a label can be defined, as we will see below
	/print "This will always execute"]:
;;

/+ eight 1]:

/!myif! if 0 [
	/print "This will never execute"]:
;myif;

\\ Else statements take two arguments, the if's label, and a code block. This means that else statements can actually be located in any location after the if statement - if the if statement fails,
\\ execution will jump to the else statement, and once that code block finishes, back to just after the if statement.
\\ Else statements, like if statements, can include a label.

/else myif [
	/print "This, however, will be printed"]:
;;

\\ PythonScript, being a linear language, lacks loops. Instead, it has jump statements. The ! operator is the jump operator.

/if /== eight 3] [ \\ Notice the == operator being used.
	!myif \\ jump to line !myif! on line 50.
;;

\\ That is the end of this pseudo-tutorial that I am calling a specification. Eventually I'll write up a proper specification.
```
