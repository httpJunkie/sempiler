---
layout : feature
video : NZlvSRcthco
title : Intrinsics
since : 0.1
targets : [C++, Swift]
---

The term intrinsics is used to describe data types that are inherent to the target platform, such as `int` or `float`.

These fundamental datatypes may not exist in the source language, or have a different name, so we use [fakeywords](fakeywords) to define them.

Here is an example of a definition in TypeScript:

| Symbol | Usage | Notes |
|--------|-------|-------|
| `type int = number` | Integer is aliased to number for arithmetic operations |  |
| `interface _int {...}` | For defining integer instance properties |  |
| `const int = number & { new() : _int }` | Value type definition |  |

**NOTE** The `number` keyword is used only in [stub APIs](../stub-apis). You should choose a more specific intrinsic type in your code.

**NOTE** This is just to illustrate how Sempiler simulates intrinsic data types. Using them in your code is **the same as any type**.

{% include agnostic.html %}

## <a name="substitutions"></a>Substitution

You may wonder why you do not see `_int` references in the emitted result. 

Sempiler allows target platforms to specify type name substitutions, to **hide front end implementation details from the back end code**.

For example, replacing `_int` with `int` during the transpilation phase.

## <a name='platform-specific'></a>Platform Specific

The intrinsics available to you depend on the symbols available on the target platform.

Target platforms will declare the intrinsic types in their respective [core stub APIs](../stub-apis#core).