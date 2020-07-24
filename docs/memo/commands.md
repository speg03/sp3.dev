# コマンド覚書

## ag

the_silver_searcher

option|help
-|-
`--noheading`|先頭行にファイル名を出力しない

## aws

```sh
# S3署名付きURLの発行
aws s3 presign --expires-in 3600 s3://bucket_name/object_key
```

## brew

Homebrew

```sh
# リポジトリの更新
brew update

# リポジトリの追加
brew tap user/repo

# パッケージの依存関係
brew deps formula

# パッケージのインストール
brew install

# パッケージの削除
brew uninstall

# パッケージの再インストール
brew reinstall

# パッケージの更新
brew upgrade

# 古いバージョンのパッケージを削除
brew cleanup
```

## curl

option|help
-|-
`-C <offset>`, `--continue-at <offset>`|部分ダウンロード<br>（`offset`に`-`を指定した場合は自動的にオフセットを検出して続きからダウンロードする）

## cut

option|help
-|-
`-d <delim>`|デリミタの指定
`-f <list>`|デリミタで分割されたカラムのうち、出力するカラム番号

## dd

```sh
# 転送の進捗を確認する
kill -USR1 <ddのプロセスID>
```

## df

ディスクごとのディスク使用量を調べる。

option|help
-|-
`-h`|ヒューマンリーダブルな単位で表示

## dstat

option|help
-|-
`-a`|デフォルトの項目
`-m`|メモリ

## du

ファイルやディレクトリごとのディスク使用量を調べる。

option|help
-|-
`-d`|ディレクトリをたどっていく深さ
`-h`|ヒューマンリーダブルな単位で表示
`-s`|指定したパスがディレクトリの場合、トータルのディスク使用量を表示する

## find

```sh
# リンク切れしたシンボリックリンクを探す
find -L /path/to/check -type l
```

## gcloud

google-cloud-sdk

```sh
# 初期化
gcloud init

# コンポーネントの更新
gcloud components update
```

## git

```sh
# Gitリポジトリのアーカイブ作成
git archive -o latest.zip HEAD

# 現在のパスがGitリポジトリかどうか
git rev-parse --is-inside-work-tree

# Gitリポジトリルートのパスを表示
git rev-parse --show-cdup
git rev-parse --show-toplevel

# コミットを指定してファイルを表示
git show REVISION:PATH

# 現在のブランチ名を表示
git symbolic-ref --short HEAD

# REVISIONのフォーマット
man gitrevisions
```

## grep

option|help
-|-
`-x`, `--line-regexp`|行全体を検索対象とする
`-f FILE`, `--file=FILE`|ファイルの各行を検索パターンとして使う

## jupyter

option|help
-|-
`--no-browser`|ブラウザを自動起動しない
`--allow-root`|rootユーザーでの起動を許可する
`--ip=IPADDR`|ListenするIPアドレス（デフォルト: `localhost`）
`--port=PORT`|Listenするポート（デフォルト: `8888`）
`--NotebookApp.token=TOKEN`|初回アクセス時に入力する認証トークン<br>（空文字`''`にすると認証なし）

```sh
# HTML形式に変換
jupyter nbconvert --to html mynotebook.ipynb
```

## last

直近のログインを確認する。

```sh
# 直近で再起動した時刻を確認
last reboot
```

## lsof

ファイルを使用しているプロセスを調べる。

## ps

option|help
-|-
`a`|すべてのプロセスを表示する
`u`|ユーザー列を表示する
`x`|ttyに紐付かないプロセスを表示する
`f`|:fontawesome-brands-linux: プロセスツリーを表示する

## rsync

option|help
-|-
`-v`, `--verbose`|詳細表示
`-a`, `--archive`|`-rlptgoD`と同じ
`-r`, `--recursive`|再帰的にたどる
`-l`, `--links`|シンボリックリンクをシンボリックリンクのままコピー
`-p`, `--perms`|パーミッションを維持する
`-t`, `--times`|タイムスタンプを維持する
`-g`, `--group`|グループを維持する
`-o`, `--owner`|オーナーを維持する
`-D`|デバイスファイルやスペシャルファイルをそのままコピー
`-c`, `--checksum`|ファイルの更新日、サイズではなくチェックサムでコピーすべきかどうかを判断<br>（ただし、1ファイルごとにチェックサムを計算するため遅くなる）
`-E`|:fontawesome-brands-linux: `--executability`と同じ
`--executability`|実行可能フラグを維持する
`-n`, `--dry-run`|ファイルコピーを実行せず何が起こるかだけ表示
`--rsync-path=PROGRAM`|リモート側で実行するrsyncのパスを指定<br>（`'sudo rsync'`を指定するとroot権限で実行することになる）
`-z`, `--compress`|転送時にデータを圧縮する
`-C`, `--cvs-exclude`|CVS関連ファイルを除外する
`-f`, `--filter=RULE`|ファイルのフィルタリングルール
`-F`|`--filter='dir-merge /.rsync-filter'`のエイリアス
`-P`|部分ダウンロード、かつ、進捗の表示

## tail

option|help
-|-
`-n NUM`|末尾`NUM`行表示する。`+NUM`とすると先頭の`NUM`行目から表示する

## tar

option|help
-|-
`x`|アーカイブの展開
`c`|アーカイブの作成
`t`|アーカイブされているファイルの一覧
`v`|詳細表示
`f`|アーカイブファイルの指定
`z`|gzipフィルター
`j`|bzip2フィルター
`-C directory`|`directory`に移動してから処理を行う

## unzip

option|help
-|-
`-d exdir`|展開先パスの指定
`-l`|アーカイブされているファイルの一覧

## wget

option|help
-|-
`-c`, `--continue`|部分ダウンロード

## xargs

option|help
-|-
`-r`, `--no-run-if-empty`|:fontawesome-brands-linux: 渡される引数がなければ実行しない<br>:fontawesome-brands-apple: このオプションはないがデフォルトで同じ挙動になる

## zip

```sh
zip [options] [zipfile [file ...]]
```

option|help
-|-
`-r`, `--recurse-paths`|`file`がディレクトリのときに、再帰的にたどって`zipfile`に追加する
