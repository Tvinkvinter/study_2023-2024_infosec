---
## Front matter
title: "Лабораторная работа № 1"
subtitle: "Установка и конфигурация
операционной системы на виртуальную машину и подготовка репозитория"
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

Целью данной работы является приобретение практических навыков
установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов, а также изучение средств контроля версий и получение навыков работы с git.

# Задание

1. Установить и настроить ОС Linux на виртуальную машину.

2. Подготовить репозиторий для дальнейшей работы.


# Теоретическое введение

- Операционная система — это комплекс программ, предназначенных для управления ресурсами компьютера и организации взаимодействия с пользователем [1].

- Системы контроля версий — это программные инструменты, помогающие командам разработчиков управлять изменениями в исходном коде с течением времени [2].

# Выполнение лабораторной работы

1. Создадим виртуальную машину (@fig:001).

![Окно создания виртуальной машины](image/screenshot_1.png){#fig:001 width=90%}

2. Запустим виртуальную машину и дождемся загрузки ОС. После этого проведем первичную настройку системы (@fig:002).

![Окно настройки ОС](image/screenshot_3.png){#fig:002 width=90%}

3. После запуска ОС откроем терминал и выведем некоторую информацию о нашей конфигурации (@fig:003 - @fig:009).

![Версия ядра Linux](image/screenshot_4.png){#fig:003 width=90%}

![Частота процессора ](image/screenshot_5.png){#fig:004 width=90%}

![Модель процессора ](image/screenshot_6.png){#fig:005 width=90%}

![Объем доступной оперативной памяти ](image/screenshot_7.png){#fig:006 width=90%}

![Тип обнаруженного гипервизора](image/screenshot_8.png){#fig:007 width=90%}

![Тип файловой системы корневого раздела](image/screenshot_9.png){#fig:008 width=90%}

![Последовательность монтирования файловых систем](image/screenshot_10.png){#fig:009 width=90%}

4. Создадим рабочую директорию (@fig:010).

![Создание рабочей директории](image/screenshot_11.png){#fig:010 width=90%}

5. Проведем базовую настройку git (@fig:011).

![Базовая настройка git](image/screenshot_12.png){#fig:011 width=90%}

6. Создадим два SSH-ключа по двум разным алгоритмам (@fig:012 - @fig:013).

![Создание ключа SSH по алгоритму rsa](image/screenshot_13.png){#fig:012 width=90%}

![Создание ключа SSH по алгоритму ed25519](image/screenshot_14.png){#fig:013 width=90%}

7. Создадим ключ GPG и добавим его в GitHub (@fig:014 - @fig:016).

![Создание ключа GPG](image/screenshot_15.png){#fig:014 width=90%}

![Создание ключа GPG](image/screenshot_16.png){#fig:015 width=90%}

![Добавление ключа GPG в Github](image/screenshot_17.png){#fig:016 width=90%}

8. Настроим автоматические подписи коммитов git (@fig:017).

![Настройка автоматических подписей коммитов git](image/screenshot_18.png){#fig:017 width=90%}

9. Авторизуемся на Github с помощью gh (@fig:018).

![Настройка gh](image/screenshot_19.png){#fig:018 width=90%}

10. Создадим репозиторий на основе данного шаблона и склонируем его на локальную машину (@fig:019 - @fig:020).

![Создание репозитория](image/screenshot_20.png){#fig:019 width=90%}

![Клонирование репозитория](image/screenshot_21.png){#fig:020 width=90%}

11. Настроим каталог курса и создадим коммит. Затем отправим изменения на сервер (@fig:021).

![Настройка каталога курса](image/screenshot_22.png){#fig:021 width=90%}

# Выводы

Были приобретены практические навыки установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов, а также изучены средства контроля версий и получены навыки работы с git.

# Список литературы{.unnumbered}

[1] https://blog.skillfactory.ru/glossary/operaczionnaya-sistema/

[2] https://www.atlassian.com/ru/git/tutorials/what-is-version-control
