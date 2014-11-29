---
layout: post
title:  "Сервис для скалолазов"
date:   2014-11-03 22:26:00
categories: jekyll update
comments: true
---

Начал делать сервис для скалолазов.
Идея сервиса заключается в возможности пользователю на основании своих данных составить оптимальную программу тренировок и отмечать свой прогресс. 

Т.к. у мой опыт программирования существенно меньше опыта администрирования БД, то разработку я начну с определения сущностей и плясать постараюсь от базы.

Сущности по моему мнению должны быть следующие:

<b>Пользователь</b>: имеет определенные <b>уровень</b> и <b>Атрибуты</b>, может иметь план тренировок (тут наверное понадобится какой-нибудь календарь).

<b>Тренировка</b>: состоит из <b>упражнений</b>

<b>Упражнение</b> — атомарная сущность, может развивать какой-нибудь атрибут (тут надо подумать).

За основу плана тренировок приму [тренировку Эрика Херста][example], она хороша тем, что состоит из нескольких тренировок, которые можно разбить на упражнения. Например:

	Фаза 3 — Максимальная сила и энергия.

	Регулярность: 2 или 3 тренировки в неделю
	Детали тренировки: Начните с постепенной разминки, используя большие зацепки на трассах близкой к вашей максимальной категории длительностью примерно на 45 минут. Используйте следующие 45-60 минут для лазания болдерингов близких к вашему пределу. Между попытками давайте отдых, вы должны быть готовы на 100% для каждой следующей попытки. Как ориентир возьмите отдых от 3 до 5 минут между каждой успешкой попыткой. Короткие ходы, на несколько движений требуют отдыха от 1 до 3 минут между попытками.
	Вы можете завершать эти тренировки несколькими упражнениями нацеленными именно на скалолазную силу и мощь. Несколько сетов кампусборда, висы на фингерборде с утяжением, подтягивания с утежелением (вес должен быть достаточным, чтобы ограничить количество повторов цифрой 5) послужат отличным дополнением. Вначале делайте 2 сета каждого упражнения и за 3 недели доведите их до 4 или 5. Не делайте больше 5 — это даст совсем немного плюсов, но вы можете сами вырыть себе яму в вопросе восстановления.	

Тут есть и отдельные упражнения (кампусборд, разминочный боулдеринг 45 минут, лазанье на пределе), есть частота повторений упражнение (2-4-5 сетов) и есть регулярность самой тренировки (2-3 раза в неделю).

Разрабатывать планирую используя TDD и, поскольку таск менеджера у меня пока нет, план разработки буду вести в блоге.

Этапы такие: 

1. тесты, модели данных, связи
2. страницы для ввода тренировок и упражнений
3. авторизация, аутентификация
4. тут подумаем что делать дальше, наверное календарь тренировок

<b>UPD</b>: работа приостановлена.


[example]: [http://iloveclimbing.ru/2013/11/trenirovka-po-skalolazaniyu/]