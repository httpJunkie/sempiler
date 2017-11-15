---
layout : feature
video : YrtDv0G0-h4
title : Terminator
since : 0.1
targets : [Swift]
---

A `terminator` is one of the rarer [fakeywords](fakeywords) that we use for indicating that the program on the target platform will **unconditionally terminate**. For example, the `die` and `exit` functions in PHP, or `fatalError` in Swift.

By declaring that a scope will terminate the program execution, we can excuse behaviour that would otherwise be invalid, such as constructors in derived classes failing to call a super constructor.

Sempiler will overlook what would otherwise be a violation only if the constructor contains a terminator function that will **unconditionally** be hit.

<script src="https://gist.github.com/ComethTheNerd/0fd1681d208ed0a98428e5806414c24f.js"> </script>

Additionally, Sempiler will allow us to adorn a constructor with the `terminator` fakeyword even though constructors generally do not have a return type annotation.

This is necessary if you are sempiling to Swift because you must indicate that a constructor **may** terminate when invoked.