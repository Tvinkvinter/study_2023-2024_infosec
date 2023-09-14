---
## Front matter
title: "Лабораторная работа № 2"
subtitle: "Дискреционное разграничение прав в Linux. Основные атрибуты"
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

Целью данной работы является получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.

# Задание

1. Создать новую учетную запись guest.

2. Выполнить ряд операций в новой учетной записи.

3. Сформировать таблицу "Установленные права и разрешенные действия".

4. Сформировать таблицу "Минимальные права для совершения операций".

# Теоретическое введение

- Операционная система — это комплекс программ, предназначенных для управления ресурсами компьютера и организации взаимодействия с пользователем [1].

- Права доступа определяют, какие действия конкретный пользователь может или не может совершать с определенным файлами и каталогами. С помощью разрешений можно создать надежную среду — такую, в которой никто не может поменять содержимое ваших документов или повредить системные файлы. [2].

# Выполнение лабораторной работы

1. Создадим учетную запись пользователя guest и зададим пароль (@fig:001).

![Создание и настройка учетной записи guest](image/screenshot_1.png){#fig:001 width=90%}

2. Войдем в систему от имени пользователя guest

3. Определим директорию, в которой мы находимся (@fig:002).

![Определение текущей директории](image/screenshot_2.png){#fig:002 width=90%}

Директория является домашней.

4. Уточним имя пользователя (@fig:003).

![Уточнение имени пользователя](image/screenshot_3.png){#fig:003 width=90%}

5. Уточним имя пользователя, его группу, а также группы, куда входит пользователь (@fig:004).

![Уточнение информации о пользователе](image/screenshot_4.png){#fig:004 width=90%}

Имя пользователя совпадает с приглашением в командной строке.

6. Просмотрим файл /etc/passwd (@fig:005).

![Содержимое файла /etc/passwd](image/screenshot_5.png){#fig:005 width=90%}

Найдем в нём свою учётную запись (@fig:006).

![Учетная запись guest в файле /etc/passwd](image/screenshot_6.png){#fig:006 width=90%}

uid = 1001, gid = 1001. Совпадают со значениями, найденными в предыдущих пунктах.

7. Определим существующие в системе директории (@fig:007).

![Существующие в системе директории](image/screenshot_7.png){#fig:007 width=90%}

Удалось получить список поддиректорий директории /home. На обеих директориях установлены права drwx------.

8. Проверим, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home (@fig:008).

![Расширенные атрибуты, установленные на поддиректориях /home](image/screenshot_8.png){#fig:008 width=90%}

Удалось увидеть расширенные атрибуты директории текущего пользователя, но не удалось увидеть атрибуты директории другого пользователя.

9. Создадим в домашней директории поддиректорию dir1 и выведем права доступа и расширенные атрибуты (@fig:009).

![Создание поддиректории и информация о ней](image/screenshot_9.png){#fig:009 width=90%}

10. Снимем с директории dir1 все атрибуты (@fig:010).

![Снятие всех атрибутов](image/screenshot_10.png){#fig:010 width=90%}

11. Попытаемся создать в директории dir1 файл file1 (@fig:011).

![Создание файла file1](image/screenshot_11.png){#fig:011 width=90%}

Мы получили отказ, так как у нас нет прав на создание. Из-за этого файл не был создан.

12. Заполним таблицу «Установленные права и разрешённые действия» (@fig:012).

![Фрагмент таблицы 2.1](image/screenshot_12.png){#fig:012 width=90%}

13. Заполним таблицу «Минимальные права для совершения операций» (@fig:013).

![Фрагмент таблицы 2.2](image/screenshot_13.png){#fig:013 width=90%}

# Выводы

В рамках данной лабораторной работы были изучены средства ограничения прав для отдельных учетных записей.

# Список литературы{.unnumbered}

[1] https://blog.skillfactory.ru/glossary/operaczionnaya-sistema/

[2] https://codechick.io/tutorials/unix-linux/unix-linux-permissions
