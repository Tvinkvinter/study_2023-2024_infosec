---
## Front matter
lang: ru-RU
title: Лабораторная работа № 2
author:
  - Тарусов Артём Сергеевич
group:
  - НФИбд-02-20, 1032201667
date: 2023, Москва

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
---


## Цели

Целью данной работы является получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.

## Задачи

1. Создать новую учетную запись guest.

2. Выполнить ряд операций в новой учетной записи.

3. Сформировать таблицу "Установленные права и разрешенные действия".

4. Сформировать таблицу "Минимальные права для совершения операций".


## Ход работы

Создадим учетную запись пользователя guest и зададим пароль.

![Создание и настройка учетной записи guest](image/screenshot_1.png){#fig:001 width=90%}

## Ход работы

Войдем в систему от имени пользователя guest

Определим директорию, в которой мы находимся.

![Определение текущей директории](image/screenshot_2.png){#fig:002 width=90%}

Директория является домашней.

## Ход работы

Уточним имя пользователя.

![Уточнение имени пользователя](image/screenshot_3.png){#fig:003 width=90%}

## Ход работы

Уточним имя пользователя, его группу, а также группы, куда входит пользователь.

![Уточнение информации о пользователе](image/screenshot_4.png){#fig:004 width=90%}

Имя пользователя совпадает с приглашением в командной строке.

## Ход работы

Просмотрим файл /etc/passwd.

![Содержимое файла /etc/passwd](image/screenshot_5.png){#fig:005 width=60%}

## Ход работы

Найдем в нём свою учётную запись.

![Учетная запись guest в файле /etc/passwd](image/screenshot_6.png){#fig:006 width=90%}

uid = 1001, gid = 1001. Совпадают со значениями, найденными в предыдущих пунктах.

## Ход работы

Определим существующие в системе директории.

![Существующие в системе директории](image/screenshot_7.png){#fig:007 width=90%}

Удалось получить список поддиректорий директории /home. На обеих директориях установлены права drwx------.

## Ход работы

Проверим, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home.

![Расширенные атрибуты, установленные на поддиректориях /home](image/screenshot_8.png){#fig:008 width=90%}

Удалось увидеть расширенные атрибуты директории текущего пользователя, но не удалось увидеть атрибуты директории другого пользователя.

## Ход работы

Создадим в домашней директории поддиректорию dir1 и выведем права доступа и расширенные атрибуты.

![Создание поддиректории и информация о ней](image/screenshot_9.png){#fig:009 width=30%}

## Ход работы

Снимем с директории dir1 все атрибуты.

![Снятие всех атрибутов](image/screenshot_10.png){#fig:010 width=70%}

## Ход работы

Попытаемся создать в директории dir1 файл file1.

![Создание файла file1](image/screenshot_11.png){#fig:011 width=90%}

Мы получили отказ, так как у нас нет прав на создание. Из-за этого файл не был создан.

## Ход работы

Заполним таблицу «Установленные права и разрешённые действия».

![Фрагмент таблицы 2.1](image/screenshot_12.png){#fig:012 width=90%}

## Ход работы

Заполним таблицу «Минимальные права для совершения операций».

![Фрагмент таблицы 2.2](image/screenshot_13.png){#fig:013 width=90%}

## Результаты

В рамках данной лабораторной работы были изучены средства ограничения прав для отдельных учетных записей.

