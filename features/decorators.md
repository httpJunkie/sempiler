---
layout : feature
video : trPhRfdD3nQ
title : Decorators
since : 0.1
targets : [Swift]
---

By now you should have a good feel for the Sempiler goals and design principles. You might be wondering why we favor [fakeywords](fakeywords) over decorators, and whether we use decorators at all.

Sempiler does support decorators but in some languages they are limited to method and declarations only (not even constructors). The decision on whether to opt for decorators over [fakeywords](fakeywords) is based on the **constraints of the source language**. 

We need to use our augmented set of *keywords* for variable types, return types and other situations. In a source language like TypeScript this would not be possible with decorators.

{% include agnostic.html %}

## <a name='struct'></a>Struct

Declaring a `struct` is implemented using a decorator because the only valid usage for it is on a class-like declaration.

[Classes](type-decls#classes) and [structs](type-decls#structs) are closely aligned semantically and so utilising a standard class-like declaration to express either construct *feels* like a low friction, comfortable solution.

## <a name='platform-specific'></a>Platform Specific

Decorators are **extensible** in Sempiler and can be provided on a platform specific basis. For example, concepts like `UIApplicationMain` in iOS are implemented using a decorator in Sempiler because it is only valid on a class-like declaration.

<script src="https://gist.github.com/ComethTheNerd/29a232318dc6bfdef6c6d4bb7fa4d5a6.js"> </script>

Target platforms will declare the applicable contextual decorators in their respective [core stub APIs](../stub-apis#core).