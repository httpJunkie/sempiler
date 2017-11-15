---
layout : feature
video : 8a-3SK_d9Ks
title : Type Decls
since : 0.1
targets : [C++, Swift]
---

Sempiler provides the *usual* distinctions for type declarations.

<script src="https://gist.github.com/ComethTheNerd/57251e7fb41f707633a3a9a330ccdb7d.js"> </script>

## <a name="classes"></a>Classes

Use the normal source language construct for declaring a class. Sempiler only supports **single inheritance** as that is a common constraint across programming languages.

### <a name="public"></a>Public

Class members are currently **public by default**, which may be contrary to the semantics of your target platform. Sempiler's origins are in TypeScript whereby members are `public` unless a contrary access modifier is explicitly provided.

A design goal of the project is to preserve the comfort of writing code in your favourite source language. In TypeScript we inherently rely on default public access that to oppose this might induce an unnecessary level of friction to developers (and add to transpile times and complexity).

However, it is perfectly possible to enforce the default member access semantics of a given target platform if it proves to be a priority for the community.

### <a name="destructors-move-and-copy"></a>Destructors, Move & Copy

At present there is **no official support** for such operations. One draft plan is to introduce more [fakeywords](fakeywords) that can be used to designate destructors, as well as **move and copy constructors**.

However, the more suitable approach may be to reserve `destructor`, `move` and `copy` member names to follow the existing `constructor` or `init` convention in many source languages. Hence we recommend you **avoid using these identifiers** for methods to avoid future breaking changes.

## <a name="structs"></a>Structs

Given the similarities of their semantics, you define structs exactly the same way as you would define a [class](#classes) in your source language except for the addition of the `@struct` [decorator](decorators):

| Symbol | Usage | Notes |
|--------|-------|-------|
| `@struct` | Placed before class keyword to designate struct  |  Not all target platforms support structs |

{% include agnostic.html %}

## <a name="inheritance"></a>Inheritance

The inheritance model will depend on the semantics of the target platform **NOT** the source language.

For example, in TypeScript (JavaScript) the `class` keyword is syntactic sugar for prototype inheritance. This means inherited members will be shadowed if the derived class declares a member of the same name.

However, Sempiler has a custom resolver for call signatures which allows for *proper* inheritance:

<script src="https://gist.github.com/ComethTheNerd/fcc329aab497855bfee344cba17c9b4d.js"> </script>

The above example code is subject to the inheritance **semantics of the target platform**, not the source language.

### <a name="overloads"></a>Overloads

Check out the dedicated [overloads documentation](overloads) for how to write overloaded methods and constructors in Sempiler.

## <a name="enums">Enums

Enums are supported, but their semantics will depend on the **target platform** when it comes to the types of values members may have.

## <a name="aliases"></a>Aliases

Sempiler allows type aliasing provided the semantics of the target platform supports it. Please use the syntax designated by your source language for such declarations.

### <a name="union-and-intersection"></a>Union & Intersection

At present you may **NOT** alias a type to a complex anonymous type such as a union or intersection. This is a future advancement, but once it lands you may still only use such declarations for target platforms that support them.

- **NOT** to be confused with how [fakeywords work](fakeywords#unions)

## <a name="namespaces">Namespaces

Namespaces are not supported by all targets, such as Swift.

In TypeScript as a source language we can leverage the `module` keyword to model the `std` C++ namespace as:

<script src="https://gist.github.com/ComethTheNerd/3f8ca6f4d367d7b499556955b5e51921.js"> </script>

{%include agnostic.html %}
