# Git hooks

This is a collecion of hooks that enforce a clean commit policy:
* `pre-commit` disables committing files on the **master** branch.
* `commit-msg` checks if a commit message follows the rules that are described in [this article](https://chris.beams.io/posts/git-commit/).
* `.git-commit-msg-template.txt` is a default template for a commit message

## Installation
Clone this repository on your device

### Commit message template
To use the commit message template you copy the .git-commit-msg-template.txt file to your home
directory (or a path that you choose).

You can set this file as the default template for your commit messages:
```bash
git config --global commit.template ~/.git-commit-msg-template.txt
```

Each time you `git commit` you will be presented the contents of the template.
If you use PhpStorm as a Git client you can use [this plugin](https://plugins.jetbrains.com/plugin/9364-commit-message-template) to make use of commit templates.

### Hooks
You can use the hooks for a specific repository or install them for each repository.
The hooks will be triggered each time you try to commit.

#### Single repository installation
Copy the `pre-commit` and `commit-msg` files to the hooks folder of your repository:
```bash
cp {pre-commit,commit-msg} path-to-your-repo/.git/hooks && chmod +x path-to-your-repo/.git/hooks/{pre-commit,commit-msg}
```

#### Global installation
Create a folder that will hold the hooks
```bash
mkdir -p ~/.git-template/hooks
git config --global init.templatedir '~/.git-template'
cp path-to-cloned-repo/{pre-commit,commit-msg} ~/.git-template/hooks
chmod +x ~/.git-template/hooks/{pre-commit,commit-msg}
```

The hooks will now be set after each `git init` or `git clone`. You can also re-run `git-init` on an existing repository to update the hooks folder.

## Configuration
* You can choose to have the branch name appended to the commit message by enabling this behavior in the git configuration:
```bash
git config git-hooks.append-branch-name true
```

By default this key will not be set and the branch name will not be appended (or if you set it to **false**).
The key accepts **true** or **false** as possible values.

* Committing on the **master** branch can be enabled with the following command:
```bash
git config git-hooks.commit-on-master true
```

By default this key will not be set and committing on the **master** branch will be disabled (or if you set it to **false**).
The key accepts **true** or **false** as possible values.

All configuration options can be setup for all of your repositories by passing the `--global` flag to the above commands.
Otherwise the configuration applies only to a single repository.