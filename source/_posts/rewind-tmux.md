title: tmux rewind
date: 2017/12/04
---

## OverView

- https://medium.com/@peterxjang/a-minimalist-guide-to-tmux-13675fb160fa

最近は、だいたいtechネタはmediumからインスパイアされることが多い。
基本的なキーバインドとかは、調べるとだいたい出てくる。

## Scroll Up/Down

- https://unix.stackexchange.com/questions/81540/how-can-i-page-up-or-down-in-tmux-with-terminal-app

Next Stepで、まず、戸惑うのはスクロールできないってことじゃないかと思う。
だいたいはトラックパッドとかでスクロールすると思うので、いきなりよくわからん挙動になってビビる。

Macユーザーのデフォルトのキーは

Prefix Key -> [ -> fn+Page Up/Page Down

である。

TODO: 後でかっこいい絵文字挿入について調べる。

## Split Pane

terminalを縦割り、二画面で使いたい。
minimalist guideによれば、コマンド多すぎて、複雑すぎるので諦めろ、とある。笑
今現在、tab切り替えで満足しているならば、splitted paneは不要である。素直に新規tabを立ち上げよう(tmuxで)

それでも使いたい場合、

縦: prefix + %
横: prefix + '

でスクリーンを割ることができるので、どうぞ。

また、paneの切り替えは

prefix + o

である。

## 現在のtmuxの設定

tipsは三つほどあると、キリがいいと思うので、三つめに自分の設定を載せる

```
unbind C-b
set-option -g prefix C-t
bind-key C-t send-prefix

# Start window numbering at 1
set -g base-index 1

set -g default-terminal "xterm-256color"
```

ほぼminimalist guideからのコピペ、、ですが、数年前から基本的にはいじっていない。
prefixの変更しただけである。たまたまtが好み。

これでみんなもhackerになれるぞ！

