# ame-config

ame-shell の設定ファイル(config.ame)の文法と値を確かめる小さなコマンド。

[ame-shell](https://github.com/TatsuyaM2667/ame-shell)(Wayland のデスクトップシェル)の一部を、単独で使えるように切り出したものです。
ame-shell は画面の要らない仕事を、1 つのことをして標準入出力でやりとりする小さなコマンドに分けています。これはその 1 つです。

## 使い方

```text
ame-config: ame-shell の設定ファイル(config.ame)を調べる。

  ame-config check [ファイル]   文法と値を確かめる。問題があれば「ファイル:行: 内容」を標準エラーへ
                                終了コード 0 問題なし / 1 警告あり / 2 読めない
  ame-config path               使う設定ファイルの場所($AME_CONFIG → $XDG_CONFIG_HOME → ~/.config)

ファイルを省くと path の場所。ame-shell は警告があっても起動する(分からない行は無視する)ので、
保存したあとに `ame-config check` で確かめると、効いていない行が分かる。
```

## ビルド

```sh
zig build -Doptimize=ReleaseSafe   # zig-out/bin/ame-config(Zig 0.13、libc だけ)
zig build test
```

## このリポジトリについて

正本は ame-shell の `src/cmd/ame-config.zig` です。このリポジトリは `scripts/split-repos.sh` が生成して同期しています。
直したいところがあれば ame-shell の方へお願いします。

ライセンス: GPL-3.0(ame-shell と同じ)
