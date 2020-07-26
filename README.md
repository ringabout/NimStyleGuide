# NimStyleGuide
The style guide for Nim which only applies to our teams' project.

## Preference

### Prefer `a == nil` to `a.isNil`

### Prefer `a.len = 0` to `a == ""`


## Style

### Long parameters

```nim
proc createIoCompletionPort*(
  FileHandle: Handle, 
  ExistingCompletionPort: Handle,
  CompletionKey: ULONG_PTR, 
  NumberOfConcurrentThreads: DWORD
): Handle {.libKernel32, importc: "CreateIoCompletionPort"}
```

## Docs requirements

```nim
proc foo(a: int, b: string): int
  ## Calculate something.
  ## Params: 
  ##         - ``a``: An int.
  ##         - ``b``: An string.
  ## Returns:
  ##         - Return results.

```
