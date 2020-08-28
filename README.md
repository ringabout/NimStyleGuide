# NimStyleGuide
The style guide for Nim only applies to our team's projects.

## Philosophy

### Explicit is better than implicit

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

## C wrapper reuqirements

C wrapper must be both standard and correct.

| ctypes             | nim types  |
|--------------------|------------|
| char               | cchar      |
| unsigned char      | cuchar     |
| signed char        | cschar     |
| short              | cshort     |
| unsigned short     | cushort    |
| int                | cint       |
| unsigned int       | cuint      |
| long               | clong      |
| unsigned long      | culong     |
| long long          | clonglong  |
| unsigned long long | culonglong |
| [const] char*      | cstring    |
| [const] void *     | pointer    |

For example,

```nim
type
  POINTER_64_INT* = uint
  INT8* = cchar
  PINT8* = ptr INT8
  INT16* = cshort
  PINT16* = ptr INT16
  INT32* = cint
  PINT32* = ptr INT32
  INT64* = int64
  PINT64* = ptr INT64
  UINT8* = cuchar
  PUINT8* = ptr UINT8
  UINT16* = cushort
  PUINT16* = ptr UINT16
```

If you want to use `ptr object` in the function declaration, use `var object` instead,

```nim
proc getQueuedCompletionStatus*(
  completionPort: Handle,
  lpNumberOfBytesTransferred: var DWORD,
  lpCompletionKey: var ULONG_PTR,
  lpOverlapped: var OVERLAPPED,
  dwMilliseconds: DWORD
): WINBOOL {.libKernel32, importc: "GetQueuedCompletionStatus"}
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
proc foo(a: int, b: string): int
  ## Calculate something.
  ## .. code-block:: Nim
  ##   assert foo(12, "ok") == 3
```

## Notes

### Your variable's name can't be as same as modules' name.

## Tests

Use `testament` instead of `unittest`.
