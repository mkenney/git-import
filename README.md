# git-import

Import one git repository into another, maintaining all commit history.

## Usage

From within any `git` repository, specify a URL or path to another repository that contains the files you want to import and the path in the current repository to put the imported files and history. This can be run from anywhere within your repository.

```sh
git-import REPO PATH
```

* `REPO` The URL or path to another repository that contains the files you want to import.
* `PATH` The path in the current repository to put the imported files and history. If `PATH` doesn't exist it will be created.

If the `REPO` argument is not a valid `git` repository, the program will exit.

If the `PATH` argument is a path outside of the current repository, the program will exit.

If the `PATH` argument points to a file or directory that exists, you will be prompted to delete the file/directory. This is irreversible.

If the imported repository has any submodule definitions, for each one you will be prompted to either import it's files and commit history, migrate the submodule definition into the the current repository, or ignore it entirely.

## Examples

Here is a very simple example demonstrating how to import a repository:

```sh
$ mkdir my-repo

$ cd my-repo
~/my-repo

$ git init
Initialized empty Git repository in ~/my-repo/.git/

$ ls -a
./  ../  .git/

$ git-import git@github.com:mkenney/git-import.git ./libs/git-import
Validating repository...
Validating url...
Validating path...
Cloning into '/tmp/git-import-1520477002930870000'...
remote: Counting objects: 23, done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 23 (delta 2), reused 0 (delta 0), pack-reused 16
Receiving objects: 100% (23/23), 6.61 KiB | 1.65 MiB/s, done.
Resolving deltas: 100% (7/7), done.
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
Rewrite 294030e5b3bec09d46b494dbd04f4b35a168d07c (7/7) (0 seconds passed, remaining 0 predicted)
Ref 'refs/heads/master' was rewritten
Updating git-import-1520477002930870000
remote: Counting objects: 32, done.
remote: Compressing objects: 100% (14/14), done.
remote: Total 32 (delta 6), reused 12 (delta 5)
Unpacking objects: 100% (32/32), done.
From /tmp/git-import-1520477002930870000
 * [new branch]      master     -> git-import-1520477002930870000/master
On branch master
nothing to commit, working tree clean

$ git log
commit 2afac3ddf0b3c2328fc2aa5a277b199a69a75f30 (HEAD -> master)
Merge: 388676f ef682fb
Author: Michael Kenney <mkenney@webbedlam.com>
Date:   Wed Mar 7 01:01:37 2018 -0700

    Merge pull request #1 from mkenney/cleanup

    cleanup

commit ef682fb1df08000e91d617d6f7b1e767db2c6a41
Author: Michael Kenney <mkenney@webbedlam.com>
Date:   Wed Mar 7 00:48:03 2018 -0700

    cleanup

commit 388676fa6b45a11d23894bce3de6f1d60a750af3
Author: Michael Kenney <michael.kenney@returnpath.com>
Date:   Thu Sep 7 19:03:34 2017 -0600

    formatting

commit 6c10c15f3fb773bc328bb5e5b31ad6653a8dee3f
Author: Michael Kenney <michael.kenney@returnpath.com>
Date:   Thu Sep 7 19:02:50 2017 -0600

    file mode
...

$
```