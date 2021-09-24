## FFI module

Cross platform foreign function interface (FFI) module.
This library can be used to load/unload shared libraries and symbols from it.

### ffi

```nelua
global ffi = @record{
  handle: pointer,
}
```

FFI record, containing a handle for the library.

### ffi.load

```nelua
function ffi.load(file: cstring): ffi
```

Loads shared library from filename `file` and returns an FFI handle.
In case the load failed, then `isloaded` will return false.

### ffi:isloaded

```nelua
function ffi:isloaded(): boolean
```

Checks weather the shared library is successfully loaded.

### ffi:get

```nelua
function ffi:get(name: cstring): pointer
```

Retrieve symbol `name` from the shared library, returning its pointer.
In case it does not exist, returns nilptr.

### ffi:unload

```nelua
function ffi:unload(): boolean
```

Unloads shared library, returns `true` when it is successfully unloaded.

---
