
Import one git repository into another, maintaining all commit history.

Usage: `git-import [repo] [path]`

From within a git repository, specify a URL or path to a repository that contains the files you want to import and the path in the current repository that you want them be stored in. This can be run from anywhere within your repository.

If the `[repo]` argument is not a valid git repository, the program will exit.

If the `[path]` argument is a path outside the current repository, the program will exit.

If the `[path]` argument points to a file or directory that exists, you will be prompted to delete the file/directory. This is irreversible.

If the imported repository has any submodule definitions, for each one you will be prompted to either import it's files and commit history, migrate the submodule definition into the the current repository, or ignore it entirely.
