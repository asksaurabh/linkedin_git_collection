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