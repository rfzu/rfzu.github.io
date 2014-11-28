---
layout: post
title:  "Установка Refinery CMS на Rails 4.1 в Windows 7"
date:   2014-10-25 22:00:00
categories: jekyll update
comments: true
---

Решил сделать сайт для одного института используя [Refinery CMS][refinery]. Из коробки она не установилась из-за с ошибки в зависимостях для гемов actionmailer и railties.

	Bundler could not find compatible versions for gem "actionmailer":
	  In Gemfile:
	    refinerycms (~> 2.1.0) x64-mingw32 depends on
	      refinerycms-authentication (= 2.1.0) x64-mingw32 depends on
	        actionmailer (< 3.3, >= 3.1.3) x64-mingw32

	    rails (= 4.1.6) x64-mingw32 depends on
	      actionmailer (4.1.6)

Поискав решение в интернете, я понял что для устранения этой проблемы требуется заменить в Gemfile гемы

	gem 'refinerycms', '~> 2.1.0'
	gem 'refinerycms-acts-as-indexed', '~> 1.0.0'

на более новые, взятые с github

	gem 'refinerycms',        github:   'refinery/refinerycms',       branch: 'master'
	gem 'refinerycms-i18n',   github:   'refinery/refinerycms-i18n',  branch: 'master'
	gem 'refinerycms-acts-as-indexed'

и добавить :x64_mingw в гем 'tzinfo-data'

	gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw]


После этого bundler update выполняется корректно. Но тут меня поджидала другая проблема: не смотря на актуальность списка гемов, из-за того что при установке Refinery CMS инсталляция прерывалась у меня на руках был пустой Rails проект. К этому моменту я уже успел поставить Refinery на другую машину с Ubuntu и видел в консоли, что при установке там выполняется довольно много разных команд, которые мне не хотелось бы запускать вручную. Конечно можно было бы перенести корректно установленное приложение на Windows машину, поправить гемы и запустить bundle update, но от этого решения тоже веяло костыльностью. В итоге я просто залез в скрипт инсталляции <code>\Ruby200-x64\lib\ruby\gems\2.0.0\gems\refinerycms-2.1.3\templates\refinery\installer.rb</code> и прописал нужные мне версии гемов прямо там.

Мораль в том, что Windows не самая приятная среда для Rails разработки. Начиная от того что вы не можете поставить RVM (я использую gem 'pik'), Unicorn и заканчивая такими вот неочевидными вещами. Вполне возможно, что в своем обучении по Rails Tutorial я мог бы увидеть меньше глюков, разрабатывай я под Linux или MacOS.

[refinery]: http://refinerycms.com/