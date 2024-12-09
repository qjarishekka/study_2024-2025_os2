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

## Создание физического тома

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

Потом я изменил таблицу разделов ядра  (рис. [-@fig:005	]) и проверил списку

		partprobe /dev/sdb
		fdisk --list /dev/sdb

![изменение и проверка таблицу разделов ядра](image/05.png){#fig:005 	width=70%}




Дальше я создал новую партицию c форматом Linux LVM с помощью утилита fdisk (рис. [-@fig:007	]).

		n
		p
		ENTER
		+100Mib
		t
		8e
		w

![создание партиции](image/07.png){#fig:007 	width=70%}

Потом я еще раз обновил таблицу разделов (рис. [-@fig:008	]).

		partprobe /dev/sdb

![обновление таблицы разделов](image/08.png){#fig:008 	width=70%}


Дальше я указал его как физический том LVM используя команду pvcreate (рис. [-@fig:009	]).

		pvcreate /dev/sdb1

![физический том LVM](image/09.png){#fig:009 	width=70%}

Потом я убедился что физический том создан успешно с помощью команды pvs (рис. [-@fig:010	]).


![проверка создания физичекского тома](image/10.png){#fig:010 	width=70%}


## Создание группы томов и логических томов

Сначала я проверил доступность физическиз томов в моей системе (рис. [-@fig:011	]).

		pvs

![проверка доступности физическиз томов](image/11.png){#fig:011 	width=70%}

Потом я создал группу томов с присвоенным ей физическим томом (рис. [-@fig:012	]).

		vgcreate vgdata /dev/sdb1
		
![создание грппы томов](image/12.png){#fig:012 	width=70%}

Дальше я убедился что группа томов была создана успешно (рис. [-@fig:014	]).

		vgs
		pvs

![проверка успеха создания группы томов](image/14.png){#fig:014 	width=70%}


Потом я создал логический том LVM с именем lvdata , который будет использовать 50% доступного диского пространства в грппу томов vgdata (рис. [-@fig:015	]).

		lvcreate -n lvdata -l 50%FREE vgdata

![создание новой группы томов lvdata использующей 50% диска ](image/15.png){#fig:015 	width=70%}

Дальше проверил успеное добавление тома  (рис. [-@fig:016	]).

		lvs
		
![провека создания новой группы томов](image/16.png){#fig:016 	width=70%}

Затем я создал файловую систему поверх логического тома (рис. [-@fig:017	]).
		
		mkfs.ext4 /dev/vgdata/lvdata

![создание файловой системы](image/17.png){#fig:017 	width=70%}

Потом я создал папку, в которой я смог смонтироват том (рис. [-@fig:018	]).
		
		mkdir -p /mnt/data

![создание папки для монтирования тома](image/18.png){#fig:018 	width=70%}

Дальше я добавил строку в файл /etc/fstab (рис. [-@fig:019	]).

		vim /etc/fstab
		a
		/dev/vgdata/lvdata /mnt/data ext4 defaults 1 2
		:wq
		

![добавление строки в файл /etc/fstab](image/19.png){#fig:019 	width=70%}

и в конце концов я проверил монтирование файловой системы, для этого, я сначала перезагрузил даемон systemd (рис. [-@fig:021	]).

		systemctl daemon-reload
		mount -a
		mount |grep /mnt
		
![монтирование и проверка файловой системы](image/21.png){#fig:021	width=70%}


## Изменение размера логических томов






(рис. [-@fig:01	]).

![Название](image/1.png){#fig:01 	width=70%}

# Выводы

Здесь кратко описываются итоги проделанной работы.

# Список литературы{.unnumbered}

::: {#refs}
:::
