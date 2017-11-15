---
layout : feature
video : _ZcmXpbPbL4
title : Fakeywords
since : 0.1
---

Fakeywords augment the lexicon of the source language, in order to represent concepts present in the target context.

For example, TypeScript does not have an `inline` keyword but we can use the fakeyword equivalent to *represent* the same concept. When that source code is sempiled to a target platform that does have function inlining, the emitter will annotate the function accordingly.

{% include agnostic.html %}

## <a name="unions"></a>(ab)uses unions

In TypeScript we can leverage the union type as a container for fakeywords, along with the actual type annotation for the associated source expression.

<script src="https://gist.github.com/ComethTheNerd/34b0d078fbc264bcc497fe225142d6df.js"> </script>

## <a name="erasure"></a>Erasure

We alias the fakeyword (eg. `foo`) to `undefined`. That way it's usage will have no influence on the type checker as **TypeScript ignores undefined types**.

| Symbol | Usage | Notes |
|--------|-------|-------|
| `type foo = undefined` | Typical fakeyword type definition |  |

Therefore the union will collapse to represent just the actual type of the associated source expression.

<script src="https://gist.github.com/ComethTheNerd/20acfcf11d0a8efa5deb9f1c9fd4e7a6.js"> </script>

## <a name="platform-specific"></a>Platform Specific

By now you will probably know that one of the core concept in sempiling is **NOT** to abstract away the target platform.

Accordingly, different target contexts will provide different fakeywords for you to leverage in your source code. For example, Swift has `required` which C++ does not.

The following table is for reference:

| Symbol | Usage | Notes |
|--------|-------|-------|
| `dict<K,V>` | [Dictionaries](dictionaries) |   |
| `inline` | Function inlining | Type annotation on function declaration return type |
| `label<T extends string>` | [Parameter labels](label) | |
| `lval<T>` | C++ LValue |   |
| `override` | Used on methods and constructors that are overrides |   |
| `opt<T>` | [Optionals](optionals) |   |
| `preproc` | [Preprocessor directives](preproc) |   |
| `ptr<T>` | [Memory pointers](memory-mgmt#pointers) |  |
| `required` | [Required](required) |   |
| `rval<T>` | C++ RValue |   |
| `terminator` | [Terminator](terminator) |   |

Plus the [intrinsic data types](intrinsics) for your target platform.