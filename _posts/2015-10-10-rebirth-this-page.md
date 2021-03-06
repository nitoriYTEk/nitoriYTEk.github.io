---
layout:	post
title:	"JekyllとBootstrapでサイトを再構築したこと"
categories:	jekyll bootstrap
---

JekyllとBootstrapでサイトを再構築した。

制作物の公開用にちょっと前に作って暫く放置してたこのサイトだが、どうやら以前はhtmlベタ書きで構築されていたらしい。

久々に「ちょっとスクリーンショットでも公開するか〜〜〜」と思って触ったら普通に死にたくなったので、楽に管理出来るように作りなおした備忘録である。

環境はxubuntu14.04。全体的に微妙に記憶を頼りに書いてる部分があるので間違ってるかもしれない。

##Jekyll
[Jekyll Simple, blog-aware, static sites](https://jekyllrb.com/)

markdownとかhtmlでcontentsだけ書いて静的サイトを構築してくれるジェネレータ。便利。

あとサイトやページの情報を構造体として持って色々できる。超便利。

###インストール

まずはruby2.0以降のインストール。何も考えずにapt-getすると古いのが入るっぽいのでなんとかする。


	$ sudo add-apt-repository -y ppa:brightbox/ruby-ng
	$ sudo apt-get update
	$ sudo apt-get -y install ruby2.2

あとこのタイミングで確か、rubyの標準ライブラリを入れた記憶がある。

gemとjekyllのインストール。

	$sudo apt-get install gem
	$sudo gem install jekyll

これでインストールできた。と思ったら、execjs,node.jsがないって怒られた。

	$sudo gem install execjs
	$sudo apt-get install nodejs

これでJekyllが動くようになった。

以下のコマンドでサンプルサイトが生成される。

	$jekyll new nitoriYTEk.github.io

##Bootstrap

[Bootsttap](http://getbootstrap.com/)

[Bootswatch](http://bootswatch.com/)

HTML,CSS,JavaScript用フレームワーク。

スマートフォン等端末にも対応しているらしいが、それよりもデザイン経験のない僕には簡単に見栄え良く出来るのがありがたい。

BootswatchはBootstrap用のテーマサイト。それなりのバリエーションがあってうれしい。今回はFlatlyというテーマを使わせていただいた。

###インストール

Bootstrapの公式からzipでダウンロード、リポジトリ内にコピーする。

あとは公式のテンプレートを参考に、head部でcss/bootstrap.min.cssを、bodyの最後でjs/bootstrap.min.jsを読みこめば準備は整った。

ところで、なんで最後でjsファイルを読んでいるんだろう。このへんの経験が浅いのでよくわかっていない…

テーマは好きなのを選んでダウンロードしたmin.cssファイルを置き換えればいいらしい。

##サイト構築

先ほど作ったサンプルサイトに手を加えてサイトを作っていく。

とりあえず、class属性を適当に付加しながらナビゲーションバーとフッターをつくる。

Bootstrap公式の[Sticky footer with navbar](http://getbootstrap.com/examples/sticky-footer-navbar/)などのサンプルがとても参考になった。

Liquid templating languageというもののおかげで、自動的にpageフォーマットのページへのリンクををナビゲーションバーに置けたりする。つよい。

###記事を書く

ここまで来たらあとは記事を書くだけだ。

_posts下に2015-10-10-rebirth-this-page.md(このページ)をつくる。jekyllのおかげで、markdownでさらさら書けばナビゲーションバーやフッターと統合してくれる。うれしい。

##アップロードする

ここから先は未来の話だ。

github pagesはjekyllによって生成されたhtmlファイルではなく、個々のリソースをpushすることでgithubのサーバー側でビルドして表示してくれる。

ということで、

	$git add -A
	$git commit -m 'publish new site'
	$git push -u origin master

うまくいってたら表示される。