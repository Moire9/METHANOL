METHANOL is a functional programming language. METHANOL has no classes, as those would be incompatible with METHANOL's function-based programming. Furthermore, METHONAL lacks namespaces. Because of the lack of functions, only primitive types are allowed - integers, floating-point numbers, Strings, and lists. Data is stored by using functions to read and write to the stack. All of METHANOL is built upon the `/` operator, which serves multiple functions (note that in METHANOL the terms function, method, and operator can be used interchangeably). It can be used to execute functions and return data from those methods.
```
main 1 [ \\ All code must be inside the main function. This function takes exactly one argument, which is a string of any command line args passed to it

	\\ Push a value onto the stack.

	/ = 1;

	\\ Read from the top of the stack

	/ < 0; \\ This is the stack number, not a location
	\\ The value is ignored here since it doesn't go anywhere

	\\ Pop x values, also reading them

	/ _ 1;

	\\ Built-in function
	/ print "Hello, World!";


	\\ Branching is achieved using special branching functions.

	/ = / if / == 1 1; [
		/ print "If this does not print, there is probably something wrong with your compiler.";
	];;
	\\ The if function returns a special reference that can be used to create else statements. 
	/ else / _ 1; [
		/ print "1 != 1";
	];

	/ 0; \\ Exit code 0
];

\\ Create a function
\\ 0 is the number of arguments
return1 0 [ \\ Code blocks are surrounded with []
	/ 1; \\ / returns it's argument
]; \\ The semicolon does not mean the end of a statement, but rather the end of arguments to a function. In most cases these are analagous.

\\ Each function has it's own stack, which is pre-populated with the passed parameters. 
identity 1 [
	/ / < 1;; \\ Return the first value on the second stack
];


```

METHANOL uses Polish notation for functions, including operators (which are just special functions).

```
/ print / + 1 4;; \\ Prints 5
```

`/` syntax:
* `/ <value>;` - return `<value>` from your current function (like the `return` keyword in other languages)
* `/ <function> <args>;` - execute the function named `<function>` passing it arguments `<args>`

METHANOL has very weak restrictions on naming. A function can be named nearly anything, as long as the name does not contain whitespace. You can even name functions things like `8` and `+`, however this will probably not end well. You can even overwrite the `/` function, but doing this would be an inherently terrible idea. Remember however, that multiple functions with the same name can exist as long as their number of arumgnets differ. This means that you can technically create your own namespaces by naming functions that have periods in their names.