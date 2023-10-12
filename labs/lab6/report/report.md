---
## Front matter
title: "Лабораторная работа № 6"
subtitle: "Мандатное разграничение прав в Linux"
author: "Тарусов Артём Сергеевич"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: false
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Развить навыки администрирования ОС Linux. Получить первое практическое знакомство с технологией SELinux1. Проверить работу SELinx на практике совместно с веб-сервером
Apache.


# Задание

1. Настроить и запустить сервер Apache.

2. Исследовать влияние параметров сервера на его работу.

# Теоретическое введение

- Операционная система — это комплекс программ, предназначенных для управления ресурсами компьютера и организации взаимодействия с пользователем [1].

- Права доступа определяют, какие действия конкретный пользователь может или не может совершать с определенным файлами и каталогами. С помощью разрешений можно создать надежную среду — такую, в которой никто не может поменять содержимое ваших документов или повредить системные файлы. [2].

# Выполнение лабораторной работы

1. Войдем в систему с полученными учётными данными и убедимся, что
SELinux работает в режиме enforcing политики targeted (@fig:001).

![Конфигурация SELinux](image/screenshot_1.png){#fig:001 width=90%}

2. Обратимся с помощью браузера к веб-серверу, запущенному на нашем
компьютере, и убедимся, что последний работает (@fig:002).

![Обращение к веб-серверу](image/screenshot_2.png){#fig:002 width=90%}

3. Найдем веб-сервер Apache в списке процессов, определим его контекст
безопасности  (@fig:003).

![Контекст безопасности веб-сервера Apache](image/screenshot_3.png){#fig:003 width=90%}

4. Посмотрим текущее состояние переключателей SELinux для Apache (@fig:004).

![Текущее состояние переключателей SELinux для Apache](image/screenshot_4.png){#fig:004 width=90%}

5. Посмотрим статистику по политике с помощью команды seinfo (@fig:005).

![Статистика по политике](image/screenshot_5.png){#fig:005 width=90%}

6. Определим тип файлов и поддиректорий, находящихся в директории
/var/www (@fig:006).

![Тип файлов и поддиректорий, находящихся в директории /var/www](image/screenshot_6.png){#fig:006 width=90%}

7. Определим тип файлов, находящихся в директории /var/www/html (@fig:007).

![Тип файлов, находящихся в директории /var/www/html](image/screenshot_7.png){#fig:007 width=90%}

8. Определим круг пользователей, которым разрешено создание файлов в
директории /var/www/html (@fig:008).

![Круг пользователей, которым разрешено создание файлов в
директории /var/www/html](image/screenshot_8.png){#fig:008 width=90%}

9. Создадим от имени суперпользователя html-файл /var/www/html/test.html  (@fig:009).

![Создание файла /var/www/html/test.html](image/screenshot_9.png){#fig:009 width=90%}

Заполним его следующим содержимым:

	<html>
	<body>test</body>
	</html>

10. Проверим контекст созданного нами файла (@fig:010).

![Работа с параметрами readfile](image/screenshot_10.png){#fig:010 width=90%}

Как видим по умолчанию присваивается контекст unconfined_u:object_r:httpd_sys_content_t:s0

11. Обратимся к файлу через веб-сервер, введя в браузере адрес
http://127.0.0.1/test.html. Убедимся, что файл был успешно отображён (@fig:011).

![Файл test.html в браузере](image/screenshot_11.png){#fig:011 width=90%}

12. Изучим справку man httpd_selinux и выясним, какие контексты файлов определены для httpd. Сопоставим их с типом файла test.html (@fig:012).

![Вызов справки и тип файла test.html](image/screenshot_12.png){#fig:012 width=90%}

13. Изменим контекст файла /var/www/html/test.html с httpd_sys_content_t на samba_share_t (@fig:013).

![Изменение контекста](image/screenshot_13.png){#fig:013 width=90%}

14.Попробуем ещё раз получить доступ к файлу через веб-сервер (@fig:014).

![Файл test.html в браузере после изменения контекста](image/screenshot_14.png){#fig:014 width=90%}

15. Просмотрим log-файлы веб-сервера Apache и системный лог-файл (@fig:015).

![Содержимое логов](image/screenshot_15.png){#fig:015 width=90%}

Как видим, нам не удалось получить доступ к файлу как раз из-за измененного контекста.

16. Попробуем запустить веб-сервер Apache на прослушивание ТСР-порта 81 (@fig:016).

![Изменение содержимого файла /etc/httpd/httpd.conf](image/screenshot_16.png){#fig:016 width=90%}

17. Выполним перезапуск веб-сервера. Сбоя не произошло (@fig:017).

![Перезапуск веб-сервера](image/screenshot_17.png){#fig:017 width=90%}

18. Проанализируем лог-файлы (@fig:018).

![Лог-файл tail -nl /var/log/messages](image/screenshot_18.png){#fig:018 width=90%}

19. Выполним команду semanage port -a -t http_port_t -р tcp 81. После этого проверим список портов командой semanage port -l | grep http_port_t
Убедимся, что порт 81 есть в списке. (@fig:019).

![Попытка добавления порта 81 в список и вывод списка допустимых портов](image/screenshot_19.png){#fig:019 width=90%}

20. Попробуем запустить веб-сервер Apache ещё раз (@fig:020).

![Повторный запуск веб-сервера](image/screenshot_20.png){#fig:020 width=90%}

21. Вернем контекст httpd_sys_cоntent__t к файлу /var/www/html/ test.html. Попробуем получить доступ к файлу через веб-сервер (@fig:021).

![Файл test.html в браузере после возвращения контекста](image/screenshot_21.png){#fig:021 width=90%}

22. Исправим обратно конфигурационный файл apache, вернув Listen 80 (@fig:022).

![Параметр Listen после возвращения значения](image/screenshot_22.png){#fig:022 width=90%}

23. Попробуем удалить привязку http_port_t к 81. Удаление невозможно(@fig:023).

![Попытка удаления привязки к порту 81](image/screenshot_23.png){#fig:023 width=90%}

24. Удалим файл /var/www/html/test.html(@fig:024).

![Удаление файла /var/www/html/test.html](image/screenshot_24.png){#fig:024 width=90%}

# Выводы

В рамках данной лабораторной работы были развиты навыки администрирования ОС Linux. Получено первое практическое знакомство с технологией SELinux1. Проверена работа SELinx на практике совместно с веб-сервером Apache.


# Список литературы{.unnumbered}

[1] https://blog.skillfactory.ru/glossary/operaczionnaya-sistema/

[2] https://codechick.io/tutorials/unix-linux/unix-linux-permissions
