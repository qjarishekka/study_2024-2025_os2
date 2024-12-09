---
## Front matter
title: "отчёта по лабораторной работе №15"
subtitle: "Управление логическими томами"
author: "Кхари Жекка Кализая Арсе"

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

Получить навыки управления логическими томами.

# Задание

1. Продемонстрировать навыки создания физических томов на LVM (см. раздел 15.4.1).
2. Продемонстрировать навыки создания группы томов и логических томов на LVM (см.
раздел 15.4.2).
3. Продемонстрировать навыки изменения размера логических томов на LVM (см. раз-
дел 15.4.3).
4. Выполнить задание для самостоятельной работы (см. раздел 15.5).
ом.



# Выполнение лабораторной работы

Сначала этой лабораторной работы я открыл терминал и получил полномочия администратора. Потом я открыл файл /etc/fstab с помощью тесктового редактора vim чтобы комментировать строку, которая автомонтирует /mnt/data  (рис. [-@fig:001	]) потом я сохранил файл

		vim /etc/fstab
		#
		:wq

![комментирование строки в файле /etc/fstab](image/01.png){#fig:001 	width=70%}

Дальше я отмонтировал /mnt/data  (рис. [-@fig:002	]).

		umount /mnt/data

![отмонтирование каталога /mnt/data](image/02.png){#fig:002 	width=70%}

Затем я убедился что я правилно отмонтировал каталог (рис. [-@fig:003	]).

		umount

![проверка отмонтирования](image/03.png){#fig:003 	width=70%}

Потом я использовал утилит fdisk чтобы удалить все партиции  (рис. [-@fig:004	]).

		fdisk /dev/sdb
		p
		ENTER
		O
		ENTER
		p
		ENTER
		w
		ENTER
		

![удаление партиций](image/04.png){#fig:004 	width=70%}

(рис. [-@fig:00	]).

![Название](image/01.png){#fig:00 	width=70%}

# Выводы

Здесь кратко описываются итоги проделанной работы.

# Список литературы{.unnumbered}

::: {#refs}
:::
