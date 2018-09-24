# Commands Reference

## ag

the_silver_searcher

* Options
    * `--noheading`: 先頭行にファイル名を出力しない

## curl

* Options
    * `-C <offset>`, `--continue-at <offset>`: 部分ダウンロード（offsetに-を指定した場合は自動的にオフセットを検出して続きからダウンロードする）

## cut

* Options
    * `-d <delim>`: デリミタの指定
    * `-f <list>`: デリミタで分割されたカラムのうち、出力するカラム番号

## dd

* 転送の進捗を確認する

```
kill -USR1 <ddのプロセスID>
```

## df

ディスクごとのディスク使用量を調べる。

* Options
    * `-h`: ヒューマンリーダブルな単位で表示

## dstat

* Options
    * `-a`: デフォルトの項目
    * `-m`: メモリ

## du

ファイルやディレクトリごとのディスク使用量を調べる。

* Options
    * `-d`: ディレクトリをたどっていく深さ
    * `-h`: ヒューマンリーダブルな単位で表示
    * `-s`: 指定したパスがディレクトリの場合、トータルのディスク使用量を表示する

## find

* リンク切れしたシンボリックリンクを探す

```
find -L /path/to/check -type l
```

refs: [Find broken symlinks and delete them](https://www.commandlinefu.com/commands/view/2369/find-broken-symlinks-and-delete-them)

## grep

* Options
    * `-x`, `--line-regexp`: 行全体を検索対象とする
    * `-f FILE`, `--file=FILE`: ファイルの各行を検索パターンとして使う

## last

* Options
    * `reboot`: 直近で再起動した時刻を確認

## lsof

ファイルを使用しているプロセスを調べる。

## ps

* Options
    * `a`: すべてのプロセスを表示する
    * `u`: ユーザー列を表示する
    * `x`: ttyに紐付かないプロセスを表示する
    * `f`: :penguin: プロセスツリーを表示する

## rsync

* Options
    * `-v`, `--verbose`: 詳細表示
    * `-a`, `--archive`: `-rlptgoD`と同じ
    * `-r`, `--recursive`: 再帰的にたどる
    * `-l`, `--links`: シンボリックリンクをシンボリックリンクのままコピー
    * `-p`, `--perms`: パーミッションを維持する
    * `-t`, `--times`: タイムスタンプを維持する
    * `-g`, `--group`: グループを維持する
    * `-o`, `--owner`: オーナーを維持する
    * `-D`: デバイスファイルやスペシャルファイルをそのままコピー
    * `-c`, `--checksum`: ファイルの更新日、サイズではなくチェックサムでコピーすべきかどうかを判断（ただし、1ファイルごとにチェックサムを計算するため遅くなる）
    * `-E`: :penguin: --executabilityと同じ
    * `--executability`: 実行可能フラグを維持する
    * `-n`, `--dry-run`: ファイルコピーを実行せず何が起こるかだけ表示
    * `--rsync-path=PROGRAM`: リモート側で実行するrsyncのパスを指定（sudo rsyncを指定するとroot権限で実行することになる）
    * `-z`, `--compress`: 転送時にデータを圧縮する
    * `-C`, `--cvs-exclude`: CVS関連ファイルを除外する
    * `-f`, `--filter=RULE`: ファイルのフィルタリングルール
    * `-F`: `--filter='dir-merge /.rsync-filter'`のエイリアス
    * `-P`: 部分ダウンロード、かつ、進捗の表示

## tail

* Options
    * `-n NUM`: 末尾NUM行表示する。+NUMとすると先頭のNUM行目から表示する。

## tar

* Options
    * `x`: アーカイブの展開
    * `c`: アーカイブの作成
    * `t`: アーカイブされているファイルの一覧
    * `v`: 詳細表示
    * `f`: アーカイブファイルの指定
    * `z`: gzipフィルター
    * `j`: bzip2フィルター

## unzip

* Options
    * `-d exdir`: 展開先パスの指定
    * `-l`: アーカイブされているファイルの一覧

## wget

* Options
    * `-c`, `--continue`: 部分ダウンロード

## xargs

* Options
    * `-r`, `--no-run-if-empty`: :penguin: 渡される引数がなければ実行しない（:apple: このオプションはないがデフォルトで同じ挙動になる）
