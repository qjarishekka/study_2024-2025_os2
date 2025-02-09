---
## Front matter
title: "отчёт по лабораторной работе №14"
subtitle: "Партиции, файловые системы, монтирование"
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

Получить навыки создания разделов на диске и файловых систем. Получить навыки
монтирования файловых систем

# Задание


1. Добавьте два диска на виртуальной машине (раздел 14.4.1).
2. Продемонстрируйте навыки создания разделов MBR с помощью fdisk (раздел 14.4.2).
3. Продемонстрируйте навыки создания логических разделов с помощью fdisk (раз-
дел 14.4.3).
4. Продемонстрируйте навыки создания раздела подкачки с помощью fdisk (раз-
дел 14.4.4).
5. Продемонстрируйте навыки создания разделов GPT с помощью gdisk (раздел 14.4.5).
6. Продемонстрируйте навыки форматирования файловой системы XFS (раздел 14.4.6).
7. Продемонстрируйте навыки форматирования файловой системы EXT4 (раздел 14.4.7).
8. Продемонстрируйте навыки ручного монтирования файловых систем (раздел 14.4.8).
9. Продемонстрируйте навыки монтирования файловых систем с помощью /etc/fstab
(раздел 14.4.9).
10. Выполните задание для самостоятельной работы (раздел 14.5).



# Выполнение лабораторной работы


## Создание виртуальных носителей

Сначала я добавил два жесткого диска на виртуальную машину (рис. [-@fig:101	]).

![новые диски](image/101.png){#fig:101	 width=70%}


Потом я открыл терминал и получил полномочия администратора (рис. [-@fig:001	]).


![терминал](image/01.png){#fig:001	 width=70%}


Дальше я выполнил команду чтобы показывать список дисков в компьютере (рис. [-@fig:002	]).

		fdisk --list

![список дисков](image/02.png){#fig:002	 width=70%}



Потом я запустил утилиту fdisk чтобы создать новые партиции в диске sdg (рис. [-@fig:003	]).

		fdisk /dev/sdg

![утилита fdisk](image/03.png){#fig:003	 width=70%}

Потом я использовал клавишу q чтобы уходить оттуда  (рис. [-@fig:004	]).

![закрытие утилиты](image/04.png){#fig:004	 width=70%}



Дальше я еще раз запустил утилиту fdisk и нажал клавишу m чтобы начинать создать новую партицию (рис. [-@fig:005	]).
 потом я нажал p чтобы смотреть список партиций(рис. [-@fig:006	]), 
 дальше n чтобы добавить новый раздел(рис. [-@fig:007	]), 
 Потом p чтобы создать основной раздел(рис. [-@fig:008	]). 
 Потом я настроил раздел, сначала я выбрал номер раздела 1(
 потом я выбрал первый сектор по умолчанию, 
 последный сектор +100M(рис. [-@fig:009	]), 
 и потом я нажал t чтобы выбрать тип раздела (в этом случае 83, Linux)(рис. [-@fig:010	])
 Затем я нажал w чтобы сохранил все (рис. [-@fig:011	]).

![fdisk](image/05.png){#fig:005	 width=70%}

![fdisk](image/06.png){#fig:006	 width=70%}

![fdisk](image/07.png){#fig:007	 width=70%}

![fdisk](image/08.png){#fig:008	 width=70%}

![fdisk](image/09.png){#fig:009	 width=70%}

![fdisk](image/10.png){#fig:010	 width=70%}

![fdisk](image/11.png){#fig:011	 width=70%}


Дальше я показал таблицу разделов и таблицу разделов диска sdg (рис. [-@fig:013	]).

		fdisk -l /dev/sdg
		cat /proc/partitions

![таблица разделов](image/13.png){#fig:013	 width=70%}


Потом я записал изменения в таблицу разделов ядра(рис. [-@fig:014	]).

		partprobe /dev/sdb

![запись изменений](image/14.png){#fig:014	 width=70%}



## Создание логических разделов

Потом я запустил еще раз утилиту fdisk  (рис. [-@fig:015	]).

		fdisk /dev/sdg

![утилита fdisk](image/15.png){#fig:015	 width=70%}

Потом я нажал n чтобы добавить новый раздел (рис. [-@fig:016	]).
Дальше e чтобы создать расширенный раздел 
Потом я выбрал все параметры по умолчанию 
Затем я еще раз я нажал n чтобы создал новый раздел 
Потом я выбрал все по умолчанию кроме последного сектора, который я указал +101M (рис. [-@fig:017	]).
и Дальше я сохранил все (рис. [-@fig:018	]). 


![утилита fdisk](image/16.png){#fig:016	 width=70%}

![утилита fdisk](image/17.png){#fig:017	 width=70%}

![утилита fdisk](image/18.png){#fig:018	 width=70%}


Потом я посмотрел список разделов и записал изменения (рис. [-@fig:021	]).

		cat /proc/partitions
		fdisk --list /dev/sdg

![запись изменений](image/21.png){#fig:021	 width=70%}


## Создание раздела подкачки

Потом я еще раз запустил fdisk но используя другой диск (рис. [-@fig:022	]).

		fdisk /dev/sdg

![fdisk](image/22.png){#fig:022	 width=70%}


Потом я добавил другой раздел с размерой 100М и типом 82 и записал на таблицу ядра(рис. [-@fig:025	]).

		partprobe /dev/sdg

![новый раздел](image/25.png){#fig:025	 width=70%}

Потом еще раз я посмотрел информацию о добавленных разделах (рис. [-@fig:027	]).

		cat /proc/partitions
		fdisk --list /dev/sdg

![информация о добавленных разделах](image/27.png){#fig:027	 width=70%}


Дальше я отформатировал раздел подкачки  (рис. [-@fig:028	]).

		mkswap /dev/sdg6

![раздел подкачки](image/28.png){#fig:028	 width=70%}


Потом я включил его на выделенное пространство (рис. [-@fig:029	]).

		swapon /dev/sdg6

![включение вновь выделенного пространства подкачки](image/29.png){#fig:029	 width=70%}


Затем я просмотрел размер пространства подкачки (рис. [-@fig:030	]).

		free -m

![размер пространства подкачки](image/30.png){#fig:03	 width=70%}


## Создание разделов GPT с помощью gdisk

Здесь я использовал другую утилиту gdisk сначала чтобы смотреть информацию  (рис. [-@fig:031	]).

		gdisk -l /dev/sdh

![gdisk](image/31.png){#fig:031	 width=70%}


Потом я начал создать другой раздел  (рис. [-@fig:032	]).

		gdisk /dev/sdh

![новый раздел](image/32.png){#fig:032	 width=70%}

Cначала я нажал n чтобы создать новый раздел (рис. [-@fig:033	]).
Потом я выбрал первый сектор по умолчанию и последный сектор +100М (рис. [-@fig:034	]).
Потом я выбрал тип 8300  (рис. [-@fig:035	]).
еще раз нажал p чтобы смотреть список разделов в диске (рис. [-@fig:037	]).
и в конце концов я нажал w чтобы сохранить изменения (потом я нажал y чтобы подвержить его) (рис. [-@fig:038	]).


![gdisk](image/33.png){#fig:033	 width=70%}

![gdisk](image/34.png){#fig:034	 width=70%}

![gdisk](image/35.png){#fig:035	 width=70%}

![gdisk](image/37.png){#fig:037	 width=70%}

![gdisk](image/38.png){#fig:038	 width=70%}


Затем я обновил таблицу разделов  (рис. [-@fig:039	]).

		partprobe /dev/sdh

![таблица разделов ядра](image/39.png){#fig:039	 width=70%}

Потом я просмотрел информацию о добавленных разделах (рис. [-@fig:040	]).

		cat /proc/partitions
		gdisk -l /dev/sdc

![информация](image/40.png){#fig:040	 width=70%}


## Форматирование файловой системы XFS


Затем я создал файловую систему xfs (рис. [-@fig:042	]).

		mkfs.xfs /dev/sdg1

![файтовая система xfs](image/42.png){#fig:042	 width=70%}

Потом я установил метки файловой системы в xfsdisk (рис. [-@fig:043	]).

		xfs_admin -L xfsdisk /dev/sdg1
		
![метки файловой системы в xfsdisk](image/43.png){#fig:043	 width=70%}


## Форматирование файловой системы EXT4

здесь я создал файловую систему EXT4 (рис. [-@fig:044	]).

		mkfs.ext4 /dev/sdg5

![файловая система EXT4](image/44.png){#fig:044	 width=70%}


потом я установил метки файловой системы в ext4disk  (рис. [-@fig:045	]).

		tune2fs -L ext4disk /dev/sdb5
		
![метки файловой системы в ext4disk ](image/45.png){#fig:045	 width=70%}


и дальше установил параметры монтирования по умолчанию  (рис. [-@fig:046	]).
	
		tune2fs -o acl,user_xattr /dev/sdg5

![параметры монтирования](image/46.png){#fig:046	 width=70%}




## Ручное монтирование файловых систем

сначала я создал каталог /mnt/tmp (рис. [-@fig:047	]).

		mkdir -p /mnt/tmp

![каталог /mnt/tmp](image/47.png){#fig:047	 width=70%}

Потом я смонтировал фалйовую систему  (рис. [-@fig:048	]).

		mount /dev/sdg5 /mnt/tmp

![монтирование файловой системы](image/48.png){#fig:048	 width=70%}

потом я проверил все (рис. [-@fig:049	]).

		mount

![проверка](image/49.png){#fig:049	 width=70%}


Потом я отмонтировал его (рис. [-@fig:051	]).

		umount /dev/sdg5

![отмонтирование](image/51.png){#fig:051	 width=70%}


Потом я еще раз проверил все (рис. [-@fig:052	]).

		mount

![проверка](image/52.png){#fig:052	 width=70%}

## Монтирование разделов с помощью /etc/fstab

В этой части сначала я создал каталог /mnt/data (рис. [-@fig:053	]).

		mkdir -p /mnt/data
		
![каталог /mnt/data](image/53.png){#fig:053	 width=70%}

Потом я посмотрел информацию об идентификаторах блочных устройств (рис. [-@fig:054	]).

		blkid

![информация об идентификаторах блочных устройств](image/54.png){#fig:054	 width=70%}

Потом я получил UUID раздела  и скопировал код  (рис. [-@fig:055	]).

		blkid /dev/sdg1
		
![UUID](image/55.png){#fig:055	 width=70%}


Дальше я открыл файл /etc/fstab и там я написал следующую строку (рис. [-@fig:056	]).

		vim /etc/fstab
		UUID=значение_идентификатора /mnt/data xfs defaults 1 2

![настройка автомонтирования](image/56.png){#fig:056	 width=70%}

потом перезапускал даемон и потом я выполнил команду mount -a (рис. [-@fig:058	]).



![mount](image/58.png){#fig:058	 width=70%}

в конце концов я проверил все изменения еще раз (рис. [-@fig:059	]).

		df -h

![Название](image/59.png){#fig:059	 width=70%}



# Выводы

в этой лабораторной работы я смотрел все команды и утилиты чтобы создать новые разделы в диске и как монтировать их чтобы его использование

# Список литературы{.unnumbered}

::: {#refs}
:::
