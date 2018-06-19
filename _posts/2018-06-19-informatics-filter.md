---
title:  "Фильтрация посылок на informatics"
date:   2018-06-19
categories: [Мета]
tags: [informatics]
---

При работе на сайте дистанционной подготовки по информатике (informatics.mccme.ru или informatics.msk.ru) часто возникает потребность отфильтровать посылки по пользователю, по языку, по вердикту.
Самим сайтом такая возможность, к сожалению, не предоставляется, но фильтр можно подобрать, просто изменяя URL.

<!--more-->

URL посылок в общем виде выглядит следующим образом

{% highlight html %}
https://informatics.msk.ru/mod/statements/view3.php?chapterid=1&submit#1
{% endhighlight %}

Здесь нас интересует часть **chapterid=1**. Это параметр фильтра посылок. Таблица ниже приводит ещё несколько параметров.

| Параметр	| Значение   |
| --------- | :--------: |
| chapterid | id задачи (можно найти на странице задачи `Задача №1664`) |
| status_id | id статуса посылки |
| user_id   | id пользователя (можно найта в url его страницы `https://informatics.msk.ru/moodle/user/view.php?id=302820`) |
| lang_id   | id компилятора |

### Статусы посылок

| id | Статус |
| -- | :----: |
| 0  | OK |
| 1  | Ошибка компиляции |
| 2  | Ошибка во время выполнения программы |
| 3  | Превышено максимальное время работы |
| 4  | Неправильный формат вывода |
| 5  | Неправильный ответ |
| 6  | Ошибка проверки, обратитесь к администраторам |
| 7  | Частичное решение |
| 8  | Зачтено/Принято |
| 9  | Проигнорировано |
| 10 | Дисквалифицировано |
| 14 | Ошибка оформления кода |

### Компиляторы

| id | Компилятор |
| -- | :----: |
| 1  | Free Pascal 3.0.2 |
| 2  | GNU C 7.2.0 |
| 3  | GNU C++ 7.2.0 |
| 7  | Turbo Pascal |
| 8  | Borland Delphi 6 - 14.5 |
| 18 | Java JDK 1.8 |
| 22 | PHP 7.1.13 |
| 23 | Python 2.7.10 |
| 24 | Perl 5.26.1 |
| 25 | Mono C# 4.8 |
| 26 | Ruby 2.4.3 |
| 27 | Python 3.6.4 |
| 28 | Haskell GHC 8.0.2 |
| 29 | FreeBASIC 1.05.0 |
| 30 | PascalABC 3.1.0.1198 |

### Пример

Например, мы хотим выбрать все мои (id=302820) посылки по задаче "1664. Суперсумма". Подходящая URL:

{% highlight html %}
https://informatics.msk.ru/mod/statements/view3.php?chapterid=1664&user_id=302820&submit#1
{% endhighlight %}

А теперь только посылки на языке Python 3:

{% highlight html %}
https://informatics.msk.ru/mod/statements/view3.php?chapterid=1664&lang_id=27&user_id=302820&submit#1
{% endhighlight %}

Или все успешные посылки по всем пользователям на языке C++:

{% highlight html %}
https://informatics.msk.ru/mod/statements/view3.php?chapterid=1664&lang_id=3&status_id=0&submit#1
{% endhighlight %}

### PS

Подобные фильтры можно применять и на других страницах. Например, нам потребовалось получить все успешные посылки пользователя на языке Free Pascal. Для примера опять же использую свой id:

{% highlight html %}
https://informatics.msk.ru/submits/view.php?user_id=302820&lang_id=1&status_id=0#1
{% endhighlight %}
