---
layout : topic
title : Stub APIS
---

A declarative (or 'stub') API is a symbolic definition of a native API or library that **exists in the target context**. 

For example, I may be working in TypeScript and want to leverage the `CoreBluetooth` framework in Swift.

I can just provide the symbols for that API in a `.d.ts` file and write **code against the contract**. 

When my TypeScript code is sempiled and built in the target context, those symbolic links will resolve correctly.

There is **no dynamic interop** between languages here, we are just using the same names and types in our source language to express our intent in the target context - this is what is meant by 'semantic transpilation'.

## <a name="composition"></a>Composition

Stub APIs have a `.d.ts` file extension in TypeScript, because we do not need to provide implementations.

In your source language insists on implementations just return any value that satisfies the type checker. The return value is arbitrary and no bearing on the emission.

## <a name="partial"></a>Partial

Stub APIs can be partially implemented, you need only provide declarations for the native symbols (ie. symbols that are implemented on the target platform) you reference in your source code.

You can incrementally add to these stubs as and when you need to throughout the life of the project.

<script src="https://gist.github.com/ComethTheNerd/a8aa6f9a35e8dc110ba408985e577cef.js"> </script>


## <a name="production"></a>Production

Even though stub APIs are lightweight and quick to produce, you may not need to write and maintain the stub API files yourself. For example:

- Your source code does not use any native symbols
- The definitions you need have been provided by another member of the Sempiler community (we encourage you to share any you write to help others!)
- You can auto generate the stub API declarations from the source code of the target platform (a future discussion beyond the scope of this topic!)

Stub APIs require little overhead to write, and give you the power of linking against libraries and functionality in the target context with **zero cost**.

## <a name="core"></a>Core

Every target platform (eg. C++) will provide a core stub API, containing intrinsic and global constructs that exist for that target construct. For example, the `__FILE__` and `__LINE__` macros. 

Remember we do not abstract away the target platform, so core symbols will only resolve if your target context declares them. 

Source code for common functionality can still be sempiled to different platforms, as long as it does not use platform-specific symbols, or those symbols exist on all targets, or it provides some other mechanism for abstracting away any target context differences.
