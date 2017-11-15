---
layout : feature
video : RaLuY8a_l8c
title : Overloads
since : 0.1
targets : [C++, Swift]
---

Some source languages do not provide an elegant way to achieve overloading. If your chosen source language inherently supports it then you can proceed with defining overloads as normal.

{% include agnostic.html %}

If you are working in a language like TypeScript function overloading is not inherently supported. Instead you often have to parse the argument types in the actual function body to *simulate* overloading which is ugly and error prone.

Sempiler provides a way to declare overloads and their respective implementations in a clean and concise syntax. Each overload will then be emitted as a separate body in the sempiled output.

{% include not-executed-in-source-lang.html %}

Instead, Sempiler defines a globally available `overloads` function:

| Symbol | Usage | Notes |
|--------|-------|-------|
| `overloads(...bodies : delegate[]) : any` | Define overloads for the enclosing context | Only valid as direct child of method or constructor body |
| `delegate = (...args : any[]) => any` | Overload delegate signature | Encapsulates all or part of an overload implementation | 

This might look daunting so let's step through it in more detail.

## <a name="signatures"></a>Signatures

In TypeScript we can already *stack signatures* on a method or constructor declaration.

This is helpful to us because the type checker will give us the correct Intellisense support for the matching signature at call sites.

Unfortunately it still leaves the ugly aforementioned argument parsing problem, but we can get around this by using `overloads`:

<script src="https://gist.github.com/ComethTheNerd/a9ab936dfb4d72ac0d7472db2d1d4932.js"> </script>

- The last declared signature in this example is known as a [**compatibility signature**](#compat-sig) or (*compat sig*), and has a special meaning
- We pass a lambda function for each declared signature (except for the *compat sig* if present)
- The lambda signature **must match** the corresponding declared signature it maps to
- The lambda signature **DOES NOT** need to include any [fakeywords](fakeywords) mentioned in the declared signature
- The order that you pass the lambdas to `overloads` must match the order of the declared signatures

## <a name="compat-sig"></a>Compat Sig

Overload signatures often have no common representation between them - their type parameters, parameters or return types can not be represented as one signature.

It is as loose as possible because the **strong typing for overloads comes from their lambda signatures**. This type safety makes lambdas a great mechanism for providing the distinct function bodies.

If we are in a context that requires us to provide a functioin body, TypeScript expects the last declared signature to sufficiently represent all overload signatures. We can get around that with the **compatibility signature**:

| Symbol | Usage | Notes |
|--------|-------|-------|
| `(...args : any) : any` | Definition of compatibility signature | Return type can be omitted if all overloads are `void` |

By placing this signature last, we provide a workaround for the type checker to be happy.

The compatibility signature is **NOT emitted** so you should not provide any implementations for it. It is **transient**.

<script src="https://gist.github.com/ComethTheNerd/1923132f9d8a25e841f97d0a03d622da.js"> </script>

<aside>
    Only use a compat sig if overload signatures have no single, common representation
</aside>

## <a name="sharing"></a>Sharing

Any statements outside of the `overloads` construct will be shared across all overload implementations

<script src="https://gist.github.com/ComethTheNerd/3332edde3a883bad0aa5406638bd5479.js"> </script>

## <a name="composition"></a>Composition

Subsequent calls to `overloads` inside the same scope will be combined in the sempiled output. This allows you to compose [shared](#sharing) logic and logic specific to a particular overload.