---
layout : feature
video : vODbPXZR8q0
title : Memory MGMT
since : 0.1
targets : [C++]
---

The following examples will assume the source language is TypeScript, but other source languages will use equivalent semantics for providing memory management constructs.

{% include agnostic.html %}

## <a name="pointers"></a>Pointers

| Symbol | Usage | Notes |
|--------|-------|-------|
| `type ptr<T> = number & { pointee : T }` | Symbolic pointer construct |  |

### <a name="addresses"></a>Addresses

| Symbol | Usage | Notes |
|--------|-------|-------|
| `addressof<T>(t : T) : ptr<T>` | Get a pointer to a datum | Type parameter is inferred from argument, you do not need to explicitly state it |

### <a name="dereferencing"></a>Dereferencing

| Symbol | Usage | Notes |
|--------|-------|-------|
| `.pointee : T` | Dereference a pointer | |

### <a name="arithmetic"></a>Arithmetic

The pointer definition aliases `number` to allow for direct arithmetic on an instance.

## <a name="new"></a>New

For the following object initialization examples we will use a placeholder `Foo` constructor call for demonstration purposes 

### <a name="stack-allocation"></a>Stack Allocation

| Symbol | Usage | Notes |
|--------|-------|-------|
| `new Foo() : Foo` | Create a stack allocated instance of `Foo` | Stack allocated memory is deallocated automatically when the enclosing stack frame is popped |

### <a name="heap-allocation"></a>Heap Allocation

| Symbol | Usage | Notes |
|--------|-------|-------|
| `heap(new Foo()) : ptr<Foo>` | Returns a pointer to a newly heap allocated instance of `Foo` | Heap allocated memory needs to be deleted explicitly |

### <a name="object-literals"></a>Object Literals

Limited support for object literals exists, and the type must be clearly stated

| Symbol | Usage | Notes |
|--------|-------|-------|
| `<Foo>{ bar : 1 }` | Create a stack allocated instance of `Foo`  | `Foo` is inferred from type assertion |
| `f : Foo = { bar : 1 }` | Create a stack allocated instance of `Foo`  |  `Foo` is inferred from left hand side type annotation |
| `{ bar : 1 } as Foo` | Create a stack allocated instance of `Foo`  | `Foo` is inferred from `as` expression |

### <a name="delete"></a>Delete

Heap allocated memory should be explicitly deleted using the original pointer returned by `heap`

| Symbol | Usage | Notes |
|--------|-------|-------|
| `delete p.pointee` | Delete the memory pointed to by `ptr` instance `p`  | Must be called on `.pointee` not `p` directly |

## <a name="example"></a>Example

<script src="https://gist.github.com/ComethTheNerd/0380b00fde1c1a55d9808e6b25746e8e.js"> </script>