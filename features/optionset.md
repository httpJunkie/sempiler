---
layout : feature
title : OptionSet
since : 0.1.2
targets : [Swift]
---

Sempiler supports `OptionSet`, a set interface to a bit set. 

| Symbol | Usage | Notes |
|--------|-------|-------|
| `OptionSet` | OptionSet type definition |  |

## <a name="example"></a>Example

Consider this example in TypeScript, a language whereby it is commonplace to represent bit sets (or 'masks', 'flags' etc) using the bitwise OR operator `|`. 

Thus, the syntax for `OptionSet` in TypeScript is the same (in order to maintain a feeling of familiarity with the source language). 

<script src="https://gist.github.com/ComethTheNerd/58407ce104d4d5b76fe6613d761e4695.js"> </script>

- **NOTE** The syntax for `OptionSet` depends on how bit sets are represented generally in your **source language**
- **NOTE** The name for this feature comes from Swift and may be renamed in future to be agnostic

{% include agnostic.html %}

## <a name="platform-specific"></a>Platform Specific

You can only use `OptionSet` if it is supported by your target platform (and has been [implemented](../latest#issues-and-requests) in Sempiler!), eg. Swift.