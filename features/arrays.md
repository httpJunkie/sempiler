---
layout : feature
video : GCVzNBj4Vq4
title : Arrays
since : 0.1
targets : [C++, Swift]
---

## <a name="platform-specific"></a>Platform Specific

| Symbol | Usage | Notes |
|--------|-------|-------|
| `Array<T>` | Array type definition |  |

**NOTE** Currently arrays cannot be used interchangeably with `ptr<T>` in TypeScript, as one might expect for targets like C++. This is intended as a future enhancement.

## <a name="dimensions"></a>Dimensions

In several modern programming languages the size of an array at any time is an implementation details taken care of by the platform. In TypeScript we cannot initialize an n dimensional array and declared the size of each dimension and their initial contents **at the same time**.

With Sempiler we have a way of doing that by writing the required dimension inside comments.

<script src="https://gist.github.com/ComethTheNerd/b90fc2216d99973dcdbb1a055ee8e6a8.js"> </script>

This has the following drawbacks:
- It is not particularly clean
- It only supports literal numeric constants

This feature may be redesigned in future if demand warrants it, based on the evolving needs of the project.