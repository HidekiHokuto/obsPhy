`Command` + `Shift` + `.` 可以显示隐藏文件、文件夹，再按一次，恢复隐藏；

finder 下使用 `Command` + `Shift` + `G` 可以前往任何文件夹，包括隐藏文件夹。

or

```sh
defaults write com.apple.finder AppleShowAllFiles -boolean true ; killall Finder
```

```sh
defaults write com.apple.finder AppleShowAllFiles -boolean false ; killall Finder
```
