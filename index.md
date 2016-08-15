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

## [Jekyll-Bootstrap](http://jekyllbootstrap.com/)

`/atom.xml`, `/rss.xml`

## [Disqus](https://disqus.com/)

* フォーラム全体のフィード - `http://{disqus_shortname}.disqus.com/latest.rss`
* スレッドのフィード - `http://{disqus_shortname}.disqus.com/{thread_slug}/latest.rss`

たとえば、[Emacs Redux](http://emacsredux.com/)の場合には、ブログ全体のコメントのフィードは[http://emacsredux.disqus.com/latest.rss](http://emacsredux.disqus.com/latest.rss)で、[which-function-mode - Emacs Redux](http://emacsredux.com/blog/2014/04/05/which-function-mode/)という記事のコメントのフィードは[http://emacsredux.disqus.com/which_function_mode_emacs_redux/latest.rss](http://emacsredux.disqus.com/which_function_mode_emacs_redux/latest.rss)となる。

Disqusのコメント欄が表示されているページで以下のスクリプトを実行すると、うまくいけばフィードのURLが得られる。ただし`thread_slug`が正確に取得できないことがある。

```javascript
(function(){
  var disqus_shortname = window.disqus_shortname || [].map.call(document.querySelectorAll('iframe[src^="http://disqus.com/embed/comments/"]'), function(i){return i.src.match(/f=(\w+)/)[1]});
  var thread_slug = window.disqus_title || document.title.replace(/(-|\s)+/g, '_').toLowerCase().replace(/[^a-z0-9_]/g, '').replace(/_{2,}/, '_');
  alert('http://{disqus_shortname}.disqus.com/latest.rss\nhttp://{disqus_shortname}.disqus.com/{thread_slug}/latest.rss'.replace(/{[^}]+}/g, function(tag){return eval(tag)});
})();
```

`thread_slug`は、[`disqus_title`](http://help.disqus.com/customer/portal/articles/472098-javascript-configuration-variables#disqus_identifier)というパラメータが与えられている場合にはそれが使われるようだ。`disqus_title`が指定されていない場合には`document.title`からslugが自動的に作成されるらしい。異なるページで同じslugになった場合には`slug_2`のように末尾に連番を振って重複が回避される。slugの生成時には英数字と一部の記号しか使われないため、タイトルに日本語が使われていると頻繁に重複が起きる。

また、DisqusのAPIからフィードのURLを取得することもできる。ページのURLからthreadを直接取得する方法はないので、[listThreadsを叩く](https://disqus.com/api/console/#!/?method=GET&endpoint=forums%2FlistThreads&since=2014-01-01T00%3A00%3A00Z&forum=foo)などの方法を取らなければならない。

## Blogger

[Blogger のフィード URL - Blogger ヘルプ](https://support.google.com/blogger/answer/97933?hl=ja)

すべての記事のフィード、すべてのコメントのフィード、特定のラベルの記事のフィード、特定の記事のコメントのフィードが提供されている。

管理者がフィードを無効にしていることもある（[サイトのフィード設定を変更する - Blogger ヘルプ](https://support.google.com/blogger/answer/42662?hl=ja)）。

## Wordpress, ライブドアブログ, FC2ブログ, アメーバブログ, seesaaブログ, Yahoo!ブログ

[【RSSフィードのURL】確認方法まとめ。Wordpress・ライブドア・FC2・Yahooブログ・その他。 : 僕の私の備忘録](http://blog.livedoor.jp/net_scope-diary/archives/7295120.html)

## [Trending repositories on GitHub](https://github.com/trending)

[GitHub unofficial trending projects RSS feeds](http://ghtrendingrss.appspot.com/)

## SoundCloud

ユーザーの投稿した音声やプレイリストは以下のURLでpodcastとして配信されている。（ユーザーの設定によってはフィードに登録されていないこともある。）

- `http://feeds.soundcloud.com/users/soundcloud:users:{user_id}/sounds.rss`
  - user_idはユーザーページで`document.querySelector('[property="twitter:app:url:googleplay"]').content.replace('soundcloud://users:', '')`を実行すると取得できる。
- `http://feeds.soundcloud.com/playlists/soundcloud:playlists:{playlist_id}/sounds.rss`
  - playlist_idはプレイリストページで`document.querySelector('[property="twitter:app:url:googleplay"]').content.replace('soundcloud://playlists:', '')`を実行すると取得できる。

<http://getrssfeed.com/>にページのURLを入力するとpodcastのURLを返してくれる。
