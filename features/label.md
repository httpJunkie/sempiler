---
layout : feature
video : CAYtxwlm31o
title : Label
since : 0.1
targets : [Swift]
---


We use `label` as a [fakeyword](fakeywords) for providing parameter labels in source languages that do not support them inherently.

- **Not** to be confused with labels for jump instructions (eg. `break` or `goto`).
- **Not** to be confused with parameter names that are used in a function body

| Symbol | Usage | Notes |
|--------|-------|-------|
| `type label<T extends string> = undefined` | Label fakeyword definition | Type parameter is used for the parameter name and only accepts `string` literal |

Parameter labelling is used in target contexts like Swift, where the label may differ from the name used for the parameter inside the function body (implementation).

Using `label` also allows the programmer to specify names that would otherwise be illegal tokens in the source language, such as `for`.

<script src="https://gist.github.com/ComethTheNerd/ab90fc7728978ccb8aa6e28c112cbb7a.js"> </script>

{% include agnostic.html %}


## <a name="inference"></a>Inference

You do not need to provide argument labels at call sites. Sempiler will infer them from the matching function declaration and they will be emitted only if required.
