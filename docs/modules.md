# es6 modules
A basic description of es6 modules and how to use them in projects.


## What are es6 modules?
es6 modules are an extension of the es5 work-around approaches
( module pattern / iife pattern / node's common.js, browsers amd/umd ).
es6 modules solve the issues these patterns addressed with two essential
keywords.

1. import ( keyword used to add exposed variables and methods of a modules API )
2. export ( keyword used to expose variables and methods of a modules API )


## How to import modules.

If you want to import specific variables and/or methods of a modules API, you
would use this particular syntax to do so:

import {foo, bar} from './foo';

This syntax is specific to the module loader, in the sense that it interprets
the specified named properties in the { ... } not as destructured props of an
object literal, but as a static syntax character specific to modules. The same
goes with the './foo' portion of the syntax. It is known as the module specifier.
And can only be a String, and not a variable which references a String.

The module loader will identify this String as reference to the specified url/ file.
The {foo, bar} identifiers must match exported module API members. Or a
Reference Error will be thrown.

You can 'rename' the identifiers you specified like so:

import { foo as fooFunc } from './foo';
// and use like this...
fooFunc();

If you've specified the module with a 'export default' keyword, then you
can opt to import that named module with this syntax:

import foo from './foo'; Or this... import { default as foo } from './foo';
// you don't have to use the { ... } in this use-case

The industry standard is to only import the specific bindings from a modules API
that you will need. It is wasteful, and you would take a performance hit
by loading the entire module API, especially if that module exposes more
bindings than you would need.
But if you would like to import the entire module API, into a single namespace
identifier you can, using the * wildcard keyname.

import * as foo from './foo';




## How to export modules.

The export keyword is either placed in front of a declaration, or used as
an operator.

// export placed in front of a declaration

const knowledge = 'expanding by reading, studying, and building';
export { knowledge }

export var bar = 'bar';

export function foo () {
    //...
}

// export the same declarations from one operator

export { knowledge, bar, foo }

These declarations are all called 'named exports', since you are essentially
exporting a name binding of the variables / functions etc.

Also, like import, you can rename a module member at the point of export.

function foo(){
    //..
}

export { foo as bar }

Keep in mind that when you export module API members, such as variables,
and functions you are not exporting the assignment or reference to that
variable or function. You are exporting a binding or pointer to that variable
or function.
So when you change the original module API member, it will be reflected
wherever the original module API member is being imported and used.

const knowledge = 'expanding by reading, studying, and building';

export { knowledge };

// later you change the value of the string knowledge to 'yo!'.
// The value of any imported version of knowledge is now changed to 'yo!'





