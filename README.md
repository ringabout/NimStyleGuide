# NimStyleGuide
The style guide for Nim only applies to our team's projects.

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

### Whether examples are runnable

If examples are runnable
```nim
proc foo(a: int, b: string): int
  ## Calculate something.
  runnableExamples:
    assert foo(12, "ok") == 3
```

Otherwise

```nim
```nim
proc foo(a: int, b: string): int
  ## Calculate something.
  ## .. code-block:: Nim
  ##   assert foo(12, "ok") == 3
```

## Tests

Use `testament` instead of `unittest`.


