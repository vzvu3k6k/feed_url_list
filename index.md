---
layout: default
title: フィードのURLリスト
---

# フィードのURLリスト

フィードは存在するのに何らかの理由でRSSのautodiscoveryが設定されていないときなどに。

## [Tumblr](https://www.tumblr.com/)

`http://{blog_name}.tumblr.com/rss/`

## [Gist](https://gist.github.com/)

`https://gist.github.com/{user_name}.atom`

## [Jekyll](http://jekyllrb.com/), [middleman-blog](https://github.com/middleman/middleman-blog/)

`/feed.xml`

## [はてなグループ](http://g.hatena.ne.jp/)のメンバー全員の日記

公式には個別の日記のフィードしか提供されていない。

[Pipes: merge hatena group](http://pipes.yahoo.com/pipes/pipe.info?_id=TssmX7bb2xGYLar_l7okhQ)を使うとよい。

## [Disqus](https://disqus.com/)

* フォーラム全体のフィード - `http://{disqus_shortname}.disqus.com/latest.rss`
* スレッドのフィード - `http://{disqus_shortname}.disqus.com/{thread_slug}/latest.rss`

たとえば、[Emacs Redux](http://emacsredux.com/)の場合には、ブログ全体のコメントのフィードは[http://emacsredux.disqus.com/latest.rss](http://emacsredux.disqus.com/latest.rss)で、[which-function-mode - Emacs Redux](http://emacsredux.com/blog/2014/04/05/which-function-mode/)という記事のコメントのフィードは[http://emacsredux.disqus.com/which_function_mode_emacs_redux/latest.rss](http://emacsredux.disqus.com/which_function_mode_emacs_redux/latest.rss)となる。

`disqus_shortname`は多くの場合`window.disqus_shortname || [].map.call(document.querySelectorAll('iframe[src^="http://disqus.com/embed/comments/"]'), function(i){return i.src.match(/f=(\w+)/)[1]})`で取得できる。

`thread_slug`は、[`disqus_title`](http://help.disqus.com/customer/portal/articles/472098-javascript-configuration-variables#disqus_identifier)というパラメータで決まっているらしい。`window.disqus_title || document.title.replace(/(-|\s)+/g, "_").toLowerCase().replace(/[^a-z0-9_]/g, "").replace(/_{2,}/, "_")`でたいてい取得できるはず。ダメだったらDisqusのアカウントを取ってApplicationを作ってAPI ConsoleからThreadのlistを取得して確認する。

## Wordpress, ライブドアブログ, Blogger, FC2ブログ, アメーバブログ, seesaaブログ, Yahoo!ブログ

[【RSSフィードのURL】確認方法まとめ。Wordpress・ライブドア・FC2・Yahooブログ・その他。 : 僕の私の備忘録](http://blog.livedoor.jp/net_scope-diary/archives/7295120.html)
