---
layout : feature
video : EL4ULtMxdIA
title : Preproc
since : 0.1
targets : [C++]
---

We utilise the `preproc` [fakeyword](fakeywords) to designate that a statement should be treated as a **preprocessor directive**.

## <a name="variables"></a>Variables

For variable declarations we specify the type as `preproc | X` where `X` is the actual data type:

<script src="https://gist.github.com/ComethTheNerd/c0a9fba21703e55a44dcd15203bfadef.js"> </script>

This will generate the equivalent to a preprocessor `#define` statement on **target platforms that support preprocessor directives**.

## <a name="macros"></a>Macros

The [stub APIs](../stub-apis) for your target platform will provide many standard macros, such as `__FILE__` and `__LINE__`.

Support for **defining your own macro functions** is a future enhancement that is not currently supported by Sempiler.

The current proposal is to use the same [define](#variables) mechanism for variables and macros, and treat those with **lambda function initializers as macros**.

{% include feature-feedback.html %}

## <a name="if"></a>If

For if statements we provide a type assertion on the condition that specifies it should be interpreted as `preproc`:

<script src="https://gist.github.com/ComethTheNerd/f20e4d0596c1655d04ffa64805ba7f66.js"> </script>

This will generate the equivalent to a preprocessor `#if` statement on **target platforms that support preprocessor directives**.

### <a name="elif"></a>Elif

You do **NOT** need to repeat `preproc` on any `else if` branches. Their preprocessor status is inferred from the root `if` statement that they belong to.

<script src="https://gist.github.com/ComethTheNerd/5209e7c8b9b87d3755701cb12c23a10f.js"> </script>

### <a name="ifdef"></a>IfDef

Support for `ifdef` is a future enhancement that is not currently supported by Sempiler.