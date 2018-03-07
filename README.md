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
