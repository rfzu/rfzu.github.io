---
layout: post
title:  "Add old blog and twitter to blog"
date:   2014-11-01 21:25:56
categories: jekyll update
comments: true
---

<!-- Put this script tag to the <head> of your page -->
<script type="text/javascript" src="//vk.com/js/api/openapi.js?115"></script>

<script type="text/javascript">
  VK.init({apiId: 4616150, onlyWidgets: true});
</script>

Понял что формата блога мне не достаточно, т.к. записи в блоге — это все же нечто довольно объемное: план на будущее, инструкция как что-то сделать, обзор. Это все здорово, но иногда хочется просто оставить небольшую заметку на полях. Пользоваться для таких вещей Jekyll'ом не очень удобно, ведь ради пары строк приходится совершать множество действий, да и формат у блога все же не тот. Для таких вещей хорошо бы подошел твиттер или мой старый самописный блог, который сейчас лежит на Heroku. Я не смог выбрать что из них лучше, поэтому добавил и то и другое.

![skrinshoot]({{ localhost:4000 }}/images/blog_n_oldblog.png)

Самописный блог продолжает лежать не Heroku, а сюда он вставлен через iframes. Сначала отображаться в фрейме приложение на Rails 4 не хотело, выдавая в фрейме ошибку:

		Refused to display 'http://site in a frame because it set 'X-Frame-Options' to 'SAMEORIGIN'.

Как я понял, ошибка появляется из-за того что в Rails по сображениям безопасности по дефолту отключена возможность отображения сайта в фрейме. Это нужно чтобы уберечься от такой штуки, как [Clickjacking][Clickjacking]

В итоге помогло добавление в код контроллера следующего кода:

{% highlight ruby %}
before_filter :allow_iframe_requests
...
def allow_iframe_requests
  response.headers.delete('X-Frame-Options')
end
{% endhighlight %}

<!-- VK like button -->
<div id="vk_like"></div>
<script type="text/javascript">
VK.Widgets.Like("vk_like", {type: "button"});
</script>

<!-- Twitter like button -->
<a href="https://twitter.com/share" class="twitter-share-button" data-url="http://rfzu.github.io/" data-via="tomatoboard">Tweet</a>
<script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0],p=/^http:/.test(d.location)?'http':'https';if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src=p+'://platform.twitter.com/widgets.js';fjs.parentNode.insertBefore(js,fjs);}}(document, 'script', 'twitter-wjs');</script>

[Clickjacking]: [http://habrahabr.ru/post/186616/]