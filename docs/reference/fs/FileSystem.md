# FileSystem

`crescent.fs` · Read and write files. Relative paths are inside the app's own storage.

## Functions

### `appendFile`

```lua
FileSystem.appendFile(path: string, text: string)
```

Adds text to the end of a file.

### `copyFile`

```lua
FileSystem.copyFile(from: string, to: string) --> boolean
```

Copies a file, replacing anything already at the new path.

### `copyFolder`

```lua
FileSystem.copyFolder(from: string, to: string) --> boolean
```

Copies a folder and everything in it.

### `createFolder`

```lua
FileSystem.createFolder(path: string) --> boolean
```

Creates a folder (and any missing parents).

### `deleteFile`

```lua
FileSystem.deleteFile(path: string) --> boolean
```

Deletes a file. Returns false if it was not there.

### `deleteFolder`

```lua
FileSystem.deleteFolder(path: string) --> boolean
```

Deletes a folder and everything in it. Returns false if it was not there.

### `exists`

```lua
FileSystem.exists(path: string) --> boolean
```

Whether a file or folder exists.

### `getFileHash`

```lua
FileSystem.getFileHash(path: string, kind?: "md5"|"sha1"|"sha256") --> string
```

A file's fingerprint as hex, for checking a download arrived whole: "sha256" unless you ask for another.

### `getFileName`

```lua
FileSystem.getFileName(path: string) --> string
```

The last part of a path.

### `getFileSize`

```lua
FileSystem.getFileSize(path: string) --> integer
```

The size of a file in bytes.

### `getFileType`

```lua
FileSystem.getFileType(path: string) --> string
```

What a file really is, read from its first bytes and not its name: "png", "jpg", "gif", "bmp", "webp", "pdf", "zip", "mp3", "mp4", "ogg", "wav", "xml", "unknown", "empty" or "none" when there is no such file.

### `isFolder`

```lua
FileSystem.isFolder(path: string) --> boolean
```

Whether the path is a folder.

### `joinPaths`

```lua
FileSystem.joinPaths(first: string, rest: string) --> string
```

Joins path parts with /.

### `listFolder`

```lua
FileSystem.listFolder(path?: string) --> string[]
```

Names in a folder, sorted.

### `moveFile`

```lua
FileSystem.moveFile(from: string, to: string) --> boolean
```

Moves or renames a file or folder.

### `readFile`

```lua
FileSystem.readFile(path: string) --> string
```

The whole file as text. "assets/..." reads the app's own assets.

### `readFileLines`

```lua
FileSystem.readFileLines(path: string) --> string[]
```

The file's lines.

### `unzipFile`

```lua
FileSystem.unzipFile(zipPath: string, intoFolder: string) --> boolean
```

Unpacks a zip into a folder, creating it if needed.

### `writeFile`

```lua
FileSystem.writeFile(path: string, text: string)
```

Writes text to a file, replacing it; creates folders as needed.

### `zipFolder`

```lua
FileSystem.zipFolder(path: string, zipPath: string) --> boolean
```

Puts a folder (or one file) into a zip. Paths inside the zip are relative to the folder.
