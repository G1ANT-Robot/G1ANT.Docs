# path

This structure stores paths to files or directories and contains the following fields:

| Field         | Type | Description                                                  |
| ------------- | ---- | ------------------------------------------------------------ |
| `name`        | text | Name of a file (with extension) or a directory               |
| `directory`   | text | Path to a directory                                          |
| `extension`   | text | Extension of a file                                          |
| `exists`      | bool | Returns `true` if a file or a directory exists               |
| `isreadonly`  | bool | Returns `true` if a file or a directory is read-only         |
| `isfile`      | bool | Returns `true` if the path points to a file                  |
| `isdirectory` | bool | Returns `true` if the path points to a directory             |
| `content`     | list | Returns a list of names of all files and directories (when the path points to a directory) |

## Example

In the following script a path variable is declared containing the path to a user’s Desktop directory.  Then all of its fields are displayed in dialog boxes:

```G1ANT
♥path = ⟦path⟧♥environment⟦USERPROFILE⟧\Desktop
dialog ‴Name: ♥path⟦name⟧, path: ♥path⟦directory⟧, ext.: ♥path⟦extension⟧‴
dialog ‴Does it exist? ♥path⟦exists⟧, Is it RO? ♥path⟦isreadonly⟧, Is it a file? ♥path⟦isfile⟧‴
dialog ‴Content: ‴♥path⟦content⟧
```

Feel free to experiment with paths provided in the `♥path` variable — when they point to files or when they end with backslash (\\) in case of directories.

Note that it’s not possible to change (write) values to individual fields. This structure is read-only: once a path variable is declared, the fields of its structure can’t be modified.

