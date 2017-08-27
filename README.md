Github's URL structure for some git objects is
```
https://github.com/OWNER/REPOSITORY/[blob|tree]/TREE-ISH/PATH
```
But `/` (forward slash) is valid (and frequently used) character in git branch names. Therefore this structure is ambiguous.

For example this repository have these two files in different branches:

| Branch | File |
| - | - |
| `some-branch` | `sub/file` |
| `e35b943c2a294e2f7ba2b0e0978e533c2f857897/sub` | `file` |

Since `some-branch` points to `e35b943c2a294e2f7ba2b0e0978e533c2f857897`, the first file should also be accessible through `…/e35b943c2a294e2f7ba2b0e0978e533c2f857897/sub/file` URL. But this URL is also canonical URL for the second file, hence ambiguity. Currently Github resolves it to the second file:


[https://github.com/odnoletkov/github-ambiguous-url/blob/e35b943c2a294e2f7ba2b0e0978e533c2f857897/sub/file](https://github.com/odnoletkov/github-ambiguous-url/blob/e35b943c2a294e2f7ba2b0e0978e533c2f857897/sub/file)

There is a certain kind of ambiguity in the git's DSL itself, but with access to repository it can usually be easily resolved. Github URL structure adds another kind of ambiguity on top of that. It is especially inconvenient since I imagine Github URLs are often processed in contexts where you don't have/want access to the repository to resolve ambiguities.
