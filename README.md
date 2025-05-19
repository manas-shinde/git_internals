# Git Demystified

[<video src="./git-internal-demo-video.mp4" controls></video>](https://github.com/manas-shinde/git_internals/blob/main/git-internal-demo-video.mp4)

Unlock the mysteries of Git with this comprehensive repository! Dive deep into the internals of Git, understand the structure of the `.git` directory, explore essential Git commands, and discover advanced concepts such as hooks, plumbing, and more.

🚀 **Key Features:**
- **.git Directory Overview:** Explore the structure of the `.git` directory, understanding its components and their roles.
- **Git Hooks:** Learn how to use and customize Git hooks to automate tasks before or after specific events.
- **Plumbing vs Porcelain Commands:** Delve into the difference between high-level porcelain commands and low-level plumbing commands.
- **Git Objects:** Understand the four types of Git objects and their significance in version control.
- **Git References:** Explore how Git uses references to track branches, tags, and remotes.
- **Git Packfiles:** Grasp the concept of packfiles and their role in optimizing storage efficiency.
- **Git gc/reflog/fsck:** Learn about Git's garbage collection, reflog, and integrity checks.

### .git Directory Overview

```shell
$ git init git_demo
Initialized empty Git repository in /tmp/git_demo/.git/

$ cd git_demo

$ tree .git
.git
├── branches
├── config
├── description
├── HEAD
├── hooks
│   ├── applypatch-msg.sample
│   ├── commit-msg.sample
│   └── ... [Truncated for brevity]
├── info
│   └── exclude
├── objects
│   ├── info
│   └── pack
└── refs
    ├── heads
    └── tags
```
- .git/config: Holds local git configuration specific to the repo.
- .git/description: Contains a description shown by gitweb.
- .git/HEAD: Points to the current branch/tag/commit.
- .git/hooks: Initial sample hooks; create your own for custom actions.
- .git/info/exclude: Repo-level gitignore separate from .gitignore.
- .git/objects: Stores all git objects.
- .git/refs: Holds references (branch/tag/stash).
- .git/logs: Created as you navigate the repo, contains logs for git reflog.
- .git/index: Holds staging area information.


## Git Hooks
Scripts executed before/after events (commit, push, etc.).
- pre-commit: Run lint/tests; prevents commit on non-zero exit code.
- post-receive: For pushing code to production.
- Enable hooks by overwriting/creating scripts in .git/hooks and making them executable.

## Git Plumbing vs Porcelain Commands

- Porcelain: User-friendly commands; frontend for git.
- Plumbing: Lower-level commands composing porcelain commands.
- Some plumbing commands: hash-object, update-index, write-tree, commit-tree, cat-file.

## Git Objects

4 Types:

- blob: Data stored by git.
- tree: Pointers to file names, contents & other trees.
- commit: Tree of changes with metadata (author, commit message, etc.).
- tag: For annotated tags with hash of tagged object (usually commits).

![git object types](./Git%20Internals%20Explained.png "a title")

## Git References

- Names pointing to sha1 hashes.
- Stored in .git/refs.
- heads: Branch references.
- tags: Tag references.
- remotes: References on remote urls added.

## Git Packfiles

- Git initially stores objects in loose object format.
- Occasionally packs loose objects into a binary file (packfile) for space efficiency.

## Git gc/reflog/fsck
### gc

- Cleans up and optimizes the repository.
- Auto gc happens occasionally as needed.

reflog

- Records changes to repo's ```HEAD``` in ```.git/logs```.
- Useful for recovering accidentally deleted branches.

fsck

- Integrity check of objects in the database.
- Identifies dangling objects.
- Useful when reflogs are unavailable.

🌐 **Contributing:**
Feel free to contribute by forking the repository and submitting pull requests. Your insights and enhancements are welcome!

📄 **License:**
This project is licensed under the [MIT License](LICENSE). Utilize, modify, and distribute according to the terms.

Let's demystify Git together! Explore the intricacies and contribute to a comprehensive resource for the Git community. 🎓🔗 #Git #VersionControl #OpenSource
