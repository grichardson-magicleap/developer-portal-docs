---
title: NativeLoader

---

# NativeLoader



**NameSpace:** 
[Editor](/versioned_docs/version-22-Feb-2023/unity-api/api/Tests.Editor/Tests.Editor.md) 








## Public Methods

### bool FreeLibrary {#bool-freelibrary}

```csharp
public bool FreeLibrary(
    IntPtr hModule
)
```


**Parameters**

| Type | Name  | Description  | 
|--|--|--|
| IntPtr |hModule||






-----------

### IntPtr GetProcAddress {#intptr-getprocaddress}

```csharp
public IntPtr GetProcAddress(
    IntPtr hModule,
    string procedureName
)
```


**Parameters**

| Type | Name  | Description  | 
|--|--|--|
| IntPtr |hModule||
| string |procedureName||






-----------

### IntPtr LoadLibrary {#intptr-loadlibrary}

```csharp
public IntPtr LoadLibrary(
    string lpFileName
)
```


**Parameters**

| Type | Name  | Description  | 
|--|--|--|
| string |lpFileName||






-----------


