Scope - a well defined set of rules for storing variables in some location and finding those variables at a later time.

The ability to store and pull values from variables is what gives a program state.

Despite the fact that javascript is categorized as a "dynamic" or "interpreted" language Js is in fact a compiled language.

  * Js is NOT compiled well in advance
  * the results of compilation are not portable among various distribution systems.
  * nevertheless, Js performs many of the same steps (often in more sophisticated ways than we are aware) of a traditional language compiler

### tokenizing/lexing

Breaking up strings of characters into meaningful chunks. `var a = 2;` breaks up into 'var', 'a', '=', '2', ';' White space is only chunked if it is meaningful.

### LHS and RHS references

Left/right hand side of an assignment. It is better to conceptually think about it as: "who's the target of the assignment (LHS)" and "who's the source of the assignment (RHS)"

Why does it matter whether we call it LHS or RHS?

The two lookups behave differently in the circumstance where the variable has not yet been declared (nto found is any scope)

```
function foo(a) {
  console.log( a + b );
  b = a;
}

foo(2);
```

When the RHS lookup happens the first time it will not be found.  This iis an "undeclared" variable because it is not found in scope.

If an LHS lookup is performed and does not find the variable in the scopes up to global
(and is NOT in strict mode) Scope will create a new varible with that name in the global scope and pass it to the engine.

`ReferenceError` is Scope resolution failure related.
`TypeError` implies that Scope resolution was successful, bu an illegal/impossible action was attempted.

Quiz
```
function foo(a) {
  var b = a;
  return a + b;
}

var c = foo;
```
1. identify all the LHS look-ups (there are 3!).
2. Identify all the RHS look-ups (there are 4!).

-----

### Nested Scope

When a variable is not found in the immediate scope, the Js engine looks in the next outer scope.  This continues until it if found or global scope is reached.

lexical scope vs dynamic scope
  * lexical scope is based on where variables and blocks of scope are authored, by you, at write time
  * dynamic scope is still used by some languages ( bash, some perl, etc)  see appendix A

  the lexing process assigns semantic meaning to tokens

![an image showing scope](https://raw.githubusercontent.com/jastuccio/You-Dont-Know-JS/master/scope%20%26%20closures/fig2.png "a simple image showing scope")

bubble 1 is he global scope. `foo` is the only identifier in it

bubble 2 is the scope of `foo` it includes 3 identifiers: `a`, `bar`, `b`

bubble 3 encompasses the scope of `bar`. `c` is the only identifier

-----

shadowing - when the same identifier name is specitied at multiple layers of the nested scope

-----

You can reference global variables as a property reference of the global object `window.a`
  
  * access a global variable which would otherwise be inaccessible due to it being shadowed.
    * non-global sha
