---
layout : feature
video : SlBpwN9a04A
title : Dictionaries
since : 0.1
targets : [Swift]
---

Many source languages provide a way of concisely declaring a dictionary type object. However, whilst some have semantics that insist the key is a `string` (or maybe even a `number`), others allow the key to be any string-like type.

## <a name='standard'></a>Standard

If you have a standard dictionary with a `string` based key then you should continue to use the **standard syntax** for declaring it in the source language. For example, in TypeScript:

<script src="https://gist.github.com/ComethTheNerd/81c6720e8ab08b4d3251aa58c74f1b40.js"> </script>

{% include agnostic.html %}

## <a name='advanced'></a>Advanced

The `dict` type enables us to declare a **string-like key type** in a source language that does not inherently allow it.

| Symbol | Usage | Notes |
|--------|-------|-------|
| `type dict<K, V> = { [k:string] : V }` | Dict definition | |

Notice that `dict` is aliased to a **standard dictionary structure**, which means we still work with it in code as if it were a `string` based key. 

<script src="https://gist.github.com/ComethTheNerd/3bc4bc0d155327ee072cc67d7300158b.js"> </script>

In the emission `K` will be used in place of `string` for declarations. This is simply type name substitution, similar to how [intrinsics](intrinsics#substitution) are implemented.

<aside>
    PREFER STRING BASED KEYS AS MUCH AS POSSIBLE
</aside>

**NOTE** This workaround is primarily to satisfy native contracts in languages that have more liberal dictionary constraints like Swift. If you are not exchanging dictionary instances with native third party code it is recommended you stick with the more common `string` based key paradigm.

