# Git commands

## 1. Git Configuration

- System Level

```
git config --system
```

- User Level

```
git config --global
```

- Project Level

```
git config
```

- Setting a few configurations

```
git config --global user.name "Your name"
git config --global user.email "Your email"
```

- To see all your configs at one place

```
git config --list
```

- To list only global/local configs

```
git config --list --global
git config --list --local
```

- To look at each individual configuration e.g your name

```
git config user.name
```

- To have a look at your `.gitconfig` file

```
code ~/.gitconfig
```

- To set VSCode as your default editor while using git.

```
git config --global core.editor "code --wait"
```

- To add colors to git messages(red, green for successful commits).

```
git config --global color.ui true
```

- To set default branch name as main

```
git config --global init.defaultbranch main
```

- To get help and see options for a particular git command.

```
For eg: git help <command-name>
> git help log
OR
> man git-log
```

## 2. Git-completion

- [Visit this](https://github.com/git/git/tree/master/contrib/completion) to have a complete look.
- Add a `.git-completion.bash` script to auto complete git commands.

```
> cd ~
> curl -o .git-completion.bash https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash
```

- Open `.bashrc` file and add these lines to the script.

```
# Tab-completions for git-branch names
if [ -f ~/.git-completion.bash ]; then
    . ~/.git-completion.bash
fi
```

## 3. Useful commands

- Initialize a project to use git.

```
git init
```

- To see git directory which keeps track of changes in your repo.

```
> cd .git
> ls -a
```

- To add all the changes made.

```
git add -A
```

- To commit the changes you made to the repository.

```
git commit -am "Your-commit-message"
```

- Commit message best practices.

1. Short single-line summary(less than 50 chars).
2. Use present tense instead of past tense.
3. Message may start with shorthand followed by the org. For eg: [css, js], "bugfix: ", "#38045 - ".
4. After one blank line, you can add decriptive message.

- To view the commits that have been made to a project.

```
git log
```

- To see more options you get with git log

```
git help log
```

- Few of the useful options with `git log`.

```
> Shows recent 5 commits.
git log -n 5

> Show commits from/until a particular date.
git log --since=2020-01-01
git log --until=2020-01-01

> Show commits of a particular author.
git log --author="Saurabh"

> Search for a commit message using grep(globally searching for regular expressions).
git log --grep="Message you want to search"
```

- A look at how the above options can be combined as well.

```
> Command that will output the last two commits that happened before September 10, 2020.
git log --until=2020-09-10 -n 2

> Output the log for all of Karen's commits labeled "refactor" during March 2019.
git log --since=2019-03-01 --until=2019-03-31 --author="Karen" --grep="refactor"
```

- To get the SHA value of the commit where HEAD pointer points to.

```
> cat .git/HEAD

This spits out a refs address. Copy that. For eg: `ref: refs/heads/main`

> cat .git/refs/heads/main
This will output the SHA value of the commit where HEAD points to.
```

```
NOTE: The .git/HEAD file indicates the branch HEAD currently points to, and the contents of the file will contain the SHA of that branch's HEAD. If you checkout another branch, the contents of .git/refs/heads/new will not change, but the .git/HEAD contents will.
```

## 4. Get going with Git Commands

- To check your current status(asking you to add the changes to staging index or git repository(committing).

```
> git status
```

- To selectively add files to your staging area(meaning to track the changes)

```
> git add <fileName1> <fileName2>...
```

- To see the differences between files before `staging`. OR . To view the changes in the `working directory`.(differences btw working tree and staging index)

```
git diff
```

- To view the changes in the `staging area`(differences btw repository and staging tree).

```
git diff --staged

OR

git diff --cached
```

- When you `delete` the files, it also get tracked. So, you need to add after deleting to the staging area and commit. In order to delete and move that change to staging area use `git rm` :

```
git rm <file_to_delete.txt>
git commit -m "file_to_delete deleted"
```

- To track `moved/renamed` file. (Renames the file and stage this change to the staging tree simultaneously)

```
git mv initial_file_name.txt final_file_name.txt
git commit -m "Rename a file"
```

## 5. Undo Changes

- Undo/Discard `working directory` changes meaning, say you made a change to a file `index.html` and you have not staged it yet and you want to discard the changes made to this file.

```
git checkout -- index.html
```

- Undo the changes made to the staging tree. (Means the changes are added to staging area but not committed and we want to restore the changes.) `OR` Unstage the changes made to the staging tree.

```
git reset HEAD <fileName1>...<fileNameN>
```

- To amend/edit the last commit you made. For eg: Your recent commit should also include one more edit. So, you made the edit to the file and staged it. Now :

```
git commit --amend -m "Merge this commit with prev commit"
```

```
NOTE: The previous commit will be deleted and the changes made to previous commit + changes made to recent commit are committed under the message "Merge this commit with prev commit".
```

- To see any commit(means what all changes it did). Copy it's SHA value and write:

```
git show <SHA-value>
```

- Similarly, to change the commit message to the recent(last) commit.

```
git commit --amend -m "Old changes with new message"
```

```
NOTE: Working of amend:
Take whatever is the old commit(to which HEAD is pointing to), bring it back down to staging area, add whatever changing has into it, and then recommit it.
```

- To revert a commit(undo changes) done in older commits. Copy the older commit `SHA-value` and run:

```
git revert <SHA-value>

It opens up the editor to see the new message and the previous commit SHA. Save the file. See, now using git log that revert has been applied to the older commit.
```

```
> NOTE: That's why make the changes atomic. So, you can revert the chnages you want to rather than reverting 50 lines of code.
```

- To remove untracked files in the working tree.

```
git clean -f

NOTE: git clean -n ,for preview of the files to be deleted.
```
