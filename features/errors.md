---
layout : feature
video : 0MuC7YzekXw
title : Errors
since : 0.1
targets : [C++, Swift]
---

## <a name="try"></a>Try

Sempiler supports the `try` construct, or the equivalent mechanism in your source language.

### <a name="catch"><a/>Catch

There is only general `catch` support at present, meaning that you cannot provide handlers for specific classes of error.

A draft plan is to support the [overloads](overloads) construct in a `catch` context to achieve this elegantly, but this will be a future enhancement.

{% include feature-feedback.html %}

### <a name="finally"><a/>Finally

There is currently no `finally` support because it is not a mechanism that all languages support. It will be coming in a future release, but it's usage will still be **predicated on target platform support**.

## <a name="throw"></a>Throw

The spec for how `throw` should work is still under review, insofar as what types of expression are allowed to be thrown. 

In languages like JavaScript and TypeScript, you may throw many more kinds of expression than in languages like Java. As with many Sempiler design decisions, the most likely implementation will validate `throw` expressions using the **semantics of the target platform**.

Error handling still has **limited support at this early stage** in the project. In any case, `try` is still useful for intercepting errors from calls to [stub APIs](../stub-apis).