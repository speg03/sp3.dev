# Git

## Configurations

Linux

```
[user]
	name = Takahiro Yano
	email = speg03@gmail.com
	signingkey = XXXXXXXXXXXXXXXX
[credential]
	helper = store --file ~/.cache/git/credentials
[commit]
	gpgsign = true
[gpg]
	program = gpg2
```

macOS

```
[user]
	name = Takahiro Yano
	email = speg03@gmail.com
	signingkey = XXXXXXXXXXXXXXXX
[commit]
	gpgsign = true
```

## Commit Messages Guide

* [Emojiで楽しく綺麗なコミットを手に入れる - Goodpatch Blog](https://goodpatch.com/blog/beautiful-commits-with-emojis/)
* [gitmoji](https://gitmoji.carloscuesta.me/)
* [How to Write a Git Commit Message](http://chris.beams.io/posts/git-commit/)
* [Styleguides - Contributing to Atom](https://github.com/atom/atom/blob/master/CONTRIBUTING.md#git-commit-messages)
* [Closing issues using keywords - GitHub Help](https://help.github.com/articles/closing-issues-using-keywords/)
* [GitHub integration - Pivotal Tracker Help Center](https://www.pivotaltracker.com/help/articles/github_integration/)

## Tips

* 現在のパスがGitリポジトリかどうか

```
git rev-parse --is-inside-work-tree
```

* Gitリポジトリルートのパスを表示

```
git rev-parse --show-cdup
git rev-parse --show-toplevel
```

* コミットを指定してファイルを表示

```
git show REVISION:PATH
```

* 現在のブランチ名を表示

```
git symbolic-ref --short HEAD
```

* REVISIONの指定方法

```
man gitrevisions
```
