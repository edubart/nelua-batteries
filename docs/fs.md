## File system module

File system module.

Contains various utilities to manages files, directories and links.

Most functions from this library returns 3 values:
* First is the operation result, which may be false or empty in case the operation failed.
* Second is an error message, in case the operation failed.
* Third is a system dependent error code, which is zero when the operation succeeds.

### fs

```nelua
global fs = @record{}
```

The file system namespace.

### fs.sep

```nelua
global fs.sep: string
```

Character separator for directories.

### fs.StatKind

```nelua
global fs.StatKind = @enum(uint32){
  INVALID = 0,
  FILE,
  DIRECTORY,
  LINK,
  SOCKET,
  PIPE,
  CHARACTER,
  BLOCK,
  OTHER,
}
```

File status kind.

### fs.StatInfo

```nelua
global fs.StatInfo = @record{
  kind: fs.StatKind,
  dev: uint64,
  ino: uint64,
  nlink: uint64,
  mode: uint32,
  uid: uint32,
  gid: uint32,
  rdev: uint64,
  size: int64,
  atime: int64,
  mtime: int64,
  ctime: int64,
  blksize: int64, -- not available in Windows
  blocks: int64, -- not available in Windows
}
```

File status information.

### fs.isdir

```nelua
function fs.isdir(path: string): boolean
```

Checks if a directory exists.

### fs.isfile

```nelua
function fs.isfile(path: string): boolean
```

Checks if a file exists.

### fs.cwdir

```nelua
function fs.cwdir(): (string, string, integer)
```

Returns the current working directory.

### fs.chdir

```nelua
function fs.chdir(path: string): (boolean, string, integer)
```

Changes the current working directory.

### fs.chmod

```nelua
function fs.chmod(path: string, mode: uint32): (boolean, string, integer)
```

Changes permissions of a file.

### fs.chown

```nelua
function fs.chown(path: string, uid: uint32, gid: uint32): (boolean, string, integer)
```

Changes ownership of a file.

### fs.mkdir

```nelua
function fs.mkdir(path: string): (boolean, string, integer)
```

Creates a directory.

### fs.mkfile

```nelua
function fs.mkfile(path: string, contents: facultative(string)): (boolean, string, integer)
```

Creates a file into `path` and write `contents`.
If `contents` is not present then an empty is created.
If the file exists, it will be overwritten.

### fs.mklink

```nelua
function fs.mklink(oldpath: string, newpath: string, hard: facultative(boolean)): (boolean, string, integer)
```

Creates a link for object `oldpath` at `newpath`.
By default symbolic links are created, unless `hardlink` is true.

### fs.rmdir

```nelua
function fs.rmdir(path: string): (boolean, string, integer)
```

Removes a directory.

### fs.rmfile

```nelua
function fs.rmfile(path: string): (boolean, string, integer)
```

Removes a file.

### fs.move

```nelua
function fs.move(oldpath: string, newpath: string): (boolean, string, integer)
```

Moves a file or directory.

### fs.touch

```nelua
function fs.touch(path: string): (boolean, string, integer)
```

Updates access and modification time of a file.

### fs.stat

```nelua
function fs.stat(path: string, linkstat: facultative(boolean)): (fs.StatInfo, string, integer)
```

Gets file status information.

### fs.readfile

```nelua
function fs.readfile(path: string): (string, string, integer)
```

Reads all contents from a file.

### fs.readlink

```nelua
function fs.readlink(path: string): (string, string, integer)
```

Reads value from a symbolic link file.

### fs.cpfile

```nelua
function fs.cpfile(oldpath: string, newpath: string): (boolean, string, integer)
```

Copies file from `oldpath` to `newpath`.
If a file exists in `newpath`, it will be overwritten.
File permissions are preserved.

---
