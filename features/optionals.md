---
layout : feature
video : uWWas2dXFI0
title : Optionals
since : 0.1
targets : [Swift]
---

Sempiler provides a construct to express optional types (in source languages that do not have them inherently) for targeting platforms that use them.

| Symbol | Usage | Notes |
|--------|-------|-------|
| `type opt<T> = T` | Symbolic optional construct |  |

We use `opt` like other [fakeywords](fakeywords), except it is aliased to `T` rather than `undefined`.

A goal of the Sempiler design is to have code feel natural to write in the source language, whilst being valid for the target context.

By aliasing `opt<T>` to `T` we can assign `T` values directly to an optional datum as if it were being boxed and unboxed automatically.

<script src="https://gist.github.com/ComethTheNerd/fe6b39a37b5eb565181958d6509973ef.js"> </script>

## <a name="parameters"></a>Parameters

<aside>
    OPTIONAL PARAMETERS ARE NOT THE SAME AS PARAMETERS WITH AN OPTIONAL TYPE
</aside>

If you are sempiling to a target platform that has strict optionality (eg. Swift) you must observe the following:

- If the parameter is optional and the default value is `null` or not provided, the parameter is `: opt<T>` **NOT** `: T`
- If the parameter is **NOT** optional but it is annotated as `opt<T>` then it may receive `null`
- If the parameter is optional but has a **non-null** default value, you must annotate it as `opt<T>` in order to pass `null` to it

## <a name="unwrapping"></a>Unwrapping

To unwrap an optional we can use a non-null assertion. In TypeScript we use the `!` postfix unary operator.

<script src="https://gist.github.com/ComethTheNerd/b8a65af9ddefc24bc723137f16f2a497.js"> </script>

{% include agnostic.html %}