# macOS

## Font Smoothing

外部ディスプレイで表示するフォントがキレイに見えないときにフォントスムージングを無効化する。（0が無効化で1, 2と強くスムージングをかけることができる）

```
defaults -currentHost write -globalDomain AppleFontSmoothing -int 0
```

現在の値を確認する

```
defaults -currentHost read -globalDomain AppleFontSmoothing
```

設定を削除する（デフォルトの状態に戻す）

```
defaults -currentHost delete -globalDomain AppleFontSmoothing
```
