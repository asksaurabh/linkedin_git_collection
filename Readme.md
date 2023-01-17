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