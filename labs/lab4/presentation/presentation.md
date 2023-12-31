---
## Front matter
lang: ru-RU
title: Лабораторная работа № 4
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

Целью данной работы является получение практических навыков работы в консоли с расширенными атрибутами файлов.

## Задачи

1. Исследовать доступность команд при установленном расширенном aтрибуте a.

2. Исследовать доступность команд при установленном расширенном aтрибуте i.


## Ход работы

От имени пользователя guest определим расширенные атрибуты файла /home/guest/dir1/file1.

![Расширенные атрибуты файла /home/guest/dir1/file1](image/screenshot_1.png){#fig:001 width=90%}

## Ход работы

Установим командой на файл file1 права, разрешающие чтение и запись для владельца файла.

![Установка прав на файл /home/guest/dir1/file1](image/screenshot_2.png){#fig:002 width=90%}

## Ход работы

Попробуем установить на файл /home/guest/dir1/file1 расширенный атрибут a от имени пользователя guest.

![Попытка установки атрибута а на файл /home/guest/dir1/file1 от имени пользователя guest](image/screenshot_3.png){#fig:003 width=90%}

## Ход работы

Откроем еще одну консоль с правами администратора. Установим на файл /home/guest/dir1/file1 расширенный атрибут a.

![Установка атрибута а на файл /home/guest/dir1/file1](image/screenshot_4.png){#fig:004 width=90%}

## Ход работы

От пользователя guest проверим правильность установления атрибута.

![Атрибуты на файл /home/guest/dir1/file1](image/screenshot_5.png){#fig:005 width=90%}

## Ход работы

Выполним дозапись в файл file1 слова «test» и выполним чтение файла file1.

![Запись и чтение файла /home/guest/dir1/file1](image/screenshot_6.png){#fig:006 width=90%}

## Ход работы

Попробуем стереть имеющуюся в файле информацию и переименовать его.

![Попытка удаления информации и переименования файла /home/guest/dir1/file1](image/screenshot_7.png){#fig:007 width=90%}

## Ход работы

Попробуем установить на файл file1 права, запрещающие чтение и запись для владельца файла. Этого сделать не удалось.

![Попытка устанавления прав на файл /home/guest/dir1/file1](image/screenshot_8.png){#fig:008 width=90%}

## Ход работы

Снимем расширенный атрибут a с файла /home/guest/dirl/file1 от
имени суперпользователя.

![Снятие атрибута а с файла /home/guest/dir1/file1](image/screenshot_9.png){#fig:009 width=90%}

## Ход работы

Повторим операции, которые нам ранее не удавалось выполнить. Теперь все операции выполняются.

![Повторение операций после снятия атрибута а](image/screenshot_10.png){#fig:010 width=90%}

## Ход работы

Повторим действия по шагам, заменив атрибут «a» атрибутом «i».

![Установка атрибута i на файл /home/guest/dir1/file1](image/screenshot_11.png){#fig:011 width=60%}

![Повторение операций после установки атрибута i](image/screenshot_12.png){#fig:012 width=60%}

Дозаписать информацию в файл не удалось

## Ход работы

![Снятие атрибута i с файла /home/guest/dir1/file1](image/screenshot_13.png){#fig:013 width=90%}

![Повторение операций после снятия атрибута i](image/screenshot_14.png){#fig:014 width=90%}


## Результаты

В рамках данной лабораторной работы были получены практические навыки работы в консоли с расширенными атрибутами файлов.
