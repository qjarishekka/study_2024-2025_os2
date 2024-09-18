---
## Front matter
title: "Шаблон отчёта по лабораторной работе"
subtitle: "Простейший вариант"
author: "Дмитрий Сергеевич Кулябов"

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
lot: true # List of tables
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
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
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

Здесь приводится формулировка цели лабораторной работы. Формулировки
цели для каждой лабораторной работы приведены в методических
указаниях.

Цель данного шаблона --- максимально упростить подготовку отчётов по
лабораторным работам.  Модифицируя данный шаблон, студенты смогут без
труда подготовить отчёт по лабораторным работам, а также познакомиться
с основными возможностями разметки Markdown.

# Задание

Здесь приводится описание задания в соответствии с рекомендациями
методического пособия и выданным вариантом.

# Теоретическое введение
                                                                              

Более подробно про Unix см. в [@tanenbaum_book_modern-os_ru; @robbins_book_bash_en; @zarrelli_book_mastering-bash_en; @newham_book_learning-bash_en].

# Выполнение лабораторной работы

я начал эту лабораторную работу откривая терминал и подключаяся к учётной записи root (рис. [-@fig:001     ]).

		su -

![подключение к учётной записи root](image/1.png){#fig:001    width=70%}

Потом я создал каталог main и third в каталоге data (рис. [-@fig:003     ]).


		mkdir -p /data/main /data/third
  
![создание каталогов main и  third](image/2.png){#fig:001    width=70%}

и затем я убедился что каталоги создались правильно и кто является владелцем (рис. [-@fig:003     ]).

		ls -l /data

![проверка каталогов](image/3.png){#fig:003    width=70%}


Потом я изменил владелцев этих каталогов с root на main и third (рис. [-@fig:004     ]).

		chgrp main /data/main
		chgrp third /data/third

![изменение владелцев](image/4.png){#fig:004    width=70%}


Дальше я еще раз посмотрел кто теперь является владелцем каталогов (рис. [-@fig:005     ]).

		ls -Al /data

![проверка владелцев](image/5.png){#fig:005    width=70%}


Потом я установил разрешения этих каталогов (рис. [-@fig:006     ]).

		chmod 770 /data/main
		chmod 770 /data/third



![установление разрешений](image/6.png){#fig:006    width=70%}

Дальше я проверал еще раз разрешения (рис. [-@fig:007     ]).

		ls -l /data
 
![проверка разрешений](image/7.png){#fig:007    width=70%}

		


Потом я открыл другой терминал и подключился к учётной записи пользователя bob который я создал на прошлую лабораторную работу, его пароль - beta1234 (рис. [-@fig:008     ]).

		su - bob

![подключение к учётной записи пользователя bob](image/8.png){#fig:008    width=70%}


Дальше я попробовал переити в каталог data/main и создать файл emptyfile (рис. [-@fig:009     ]).

		cd /data/main
		touch emptyfile
		ls -Al


![создание каталогов в каталоге main](image/9.png){#fig:009    width=70%}

я смог создать этот файл потому что все в группе main являются владелцами каталога main


Потои я еще раз открыл новый термирнал и подключился к учетной записи alice, её пароль - alfa1234 (рис. [-@fig:011     ]).

		su - alice

![новый терминал](image/11.png){#fig:011    width=70%}

Потом я перешел в каталог /data/main (рис. [-@fig:012   ]).

		cd /data/main
		
![перемещение в каталог cd /data/main](image/12.png){#fig:012    width=70%}


Дальше я создал файлы alice1 и alice2 (рис. [-@fig:013     ]).

		touch alice1
		touch alice2
		ls -Al /data/main

![создание файлов](image/13.png){#fig:013    width=70%}


Потом я открыл новый терминал и подключился к учётной записи пользователя bob (рис. [-@fig:014     ]).

		su - bob

![новый терминал с пользователем bob](image/14.png){#fig:01    width=70%}


Дальше я перешел в каталог /data/main (рис. [-@fig:015    ]).

		cd /data/main
		
![перемещение в каталог data/main](image/15.png){#fig:015    width=70%}

Потом я смотрел какие файлы там находятся (рис. [-@fig:016    ]).

		ls -l

![просмотр файлов в каталоге /data/main](image/16.png){#fig:016    width=70%}


потом я удалил все файлы пользователя alice (рис. [-@fig:017    ]).

		rm -f alice*

![удаление файлов](image/17.png){#fig:017    width=70%}


Потом я создал два файла с пользователем bob (bob1 и bob2) (рис. [-@fig:018    ]).

		touch bob1
		touch bob2

![создание файлов bob1 и bob2](image/18.png){#fig:018    width=70%}

потом в терминале под ползователем root я установил бит идентификатора группы для каталога /data/main, а также stiky-bit для разделяемого каталога группы (рис. [-@fig:0189    ]).

		chmod g+s,o+t /data/main

![установление каталогов](image/19.png){#fig:019    width=70%}


Потом в терминале под пользователем alice я создал в каталоге /data/main файлы alice3 и alice 4 (рис. [-@fig:020    ]).


		touch alice3
		touch alice4
		ls -l

![создание файлов alice3 и alice4](image/20.png){#fig:020    width=70%}


Дальше в терминале под пользователем alice я попробовал удалить файлы bob1 и bob2 (рис. [-@fig:021    ]).

		rm -rf bob*

![удаление файлов ](image/21.png){#fig:021    width=70%}

конечно это действие запрещено потому что у alicа нет доступа на эти файлы










(рис. [-@fig:02    ]).

![Название рисунка](image/placeimg_800_600_tech.png){#fig:02    width=70%}

# Выводы

Здесь кратко описываются итоги проделанной работы.

# Список литературы{.unnumbered}

::: {#refs}
:::
