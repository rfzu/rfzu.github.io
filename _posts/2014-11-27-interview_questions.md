---
layout: post
title:  "Задачки на собеседовании на позицию Ruby / Rails junior"
date:   2014-11-27 18:26:00
categories: jekyll update
comments: true
---

На этой неделе был на 2 собеседованиях и хочу описать те вопросы, которые мне задавали. В первую очередь просят решить короткую задачку на Ruby.

Написать факториал. Я сначала написал так:

{% highlight ruby %}
def fact(n)
  fact = 1
  (1..n).each {|i| fact = fact*i}
end
{% endhighlight %}

Потом попросили написать факториал, как рекурсивную функцию:

{% highlight ruby %}
def fact(n)
  n > 1 ? n * fact(n-1) : 1
end
{% endhighlight %}

Была задачка написать функцию, которая выдавала бы случайное значение от 0 до 6 пользуясь функцией rand(4):

{% highlight ruby %}
def rand2()
  r = rand(4)
  return 0 if (r == 0 || r == 1)
  1
end

def rand7()
  r = rand2()
  r = rand(4) + r*4
  rand7() if r == 7
  r
end
{% endhighlight %}

Есть произвольный массив целых чисел и исходное число. Требуется найти в массиве число равное по модулю исходному числу, если его нет, то нужно написать то число, которое ближе всего по модулю к исходному. Если таких чисел несколько - взять то что ближе к началу:.

{% highlight ruby %}
def foo(a, b)
  delta = (a[0].abs - b).abs + 1
  a.each do |i|
    if (delta>0 and (i.abs - b).abs < delta)
      delta = (i.abs - b).abs
      @c = i
    end
    return i if delta == 0
  end
  return @c
end
{% endhighlight %}

В ходе ответа был задан вопрос знаю ли я про MapReduce. Уже после собеседования знакомый программист выдал такой вариант решения задачи, покритиковав мой код как нерубироидный и неидиоматичный:

{% highlight ruby %}
abs_x = x.abs
deltas = ary.map do |y|
  abs_y = y.abs
  abs_x > abs_y ? abs_x - abs_y : abs_y - abs_x
end
puts deltas.zip(ary).sort[0][-1]
{% endhighlight %}


	[-+]?\d*\.?[0-9]+([eE][-+]?[0-9]+)?