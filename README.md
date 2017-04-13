# Git hooks

This is a collecion of hooks that enforce a clean commit policy:
    * `pre-commit` disables committing files on the *master* branch.
    * `commit-msg` checks if a commit message follows the rules that are described in [this article](https://chris.beams.io/posts/git-commit/) and append the branch name to the commit message.
    * `.git-commit-msg-template.txt` is a template for a commit message

## Installation
Clone this repository and copy the .git-commit-msg-template.txt file to your home
directory (or a path that you choose).

You can set this file as the default template for your commit messages:
```bash
git config --global commit.template ~/.git-commit-msg-template.txt
```

Next you can copy the `pre-commit` and `commit-msg` files to the hooks folder of your repository:
```bash
cp pre-commit path-to-your-repo/.git/hooks && chmod +x path-to-your-repo/.git/hooks
```

The hooks will be triggered each time you try to commit.