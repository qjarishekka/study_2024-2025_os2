---
## Front matter
title: "отчёт по лабораторной работе №11"
subtitle: "Управление загрузкой системы"
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

Получить навыки работы с загрузчиком системы GRUB2
# Задание

1. Продемонстрируйте навыки по изменению параметров GRUB и записи изменений
в файл конфигурации (см. раздел 11.4.1).

2. Продемонстрируйте навыки устранения неполадок при работе с GRUB (см. раз-
дел 11.4.2).

3. Продемонстрируйте навыки работы с GRUB без использования root (см. раздел 11.4.3)


# Выполнение лабораторной работы

Сначала лабораторной работы я открыл терминал и получил полномочия администратора
(рис. [-@fig:001	]).

		su -

![терминал](image/01.png){#fig:001	 width=70%}

Потом я открыл файл /etc/default/grub с помощью текстового редактора vim и там я изменил строку GRUB_TIMEOUT=5 на GRUB_TIMEOUT=10 (рис. [-@fig:002	]).
 
		vim /etc/default/grub
		GRUB_TIMEOUT=10


![файл grub](image/02.png){#fig:002	 width=70%}




Потом я выполнил следующие команды (рис. [-@fig:003	]).

		grub2-mkconfig > /boot/grub2/grub.cfg
		grub2-mkconfig -o /boot/grub2/grub.cfg
		
![изменение в GRUB2](image/03.png){#fig:003	 width=70%}

Потом я изменил файл /etc/default/grub  и в строке (GRUB_CMDLINE_LINUX) я удалил параметры rhgb и quiet
 (рис. [-@fig:004	]).
		
		vim /etc/default/grub
		rhgb quiet
		:qv

![изменение файла](image/04.png){#fig:004	 width=70%}


как только появилась опция для выбора ядра, я выбрал первый и нажал 'e' чтобы открывать текстовый редактор. 
(рис. [-@fig:005	]).

		e

![редактор при загрузке](image/05.png){#fig:005	 width=70%}


Потом я добавил параметры systemd.unit=rescue.target и удалил параметры rhgb и quiet

(рис. [-@fig:006	]).

		systemd.unit=rescue.target 

![изменение параметров](image/06.png){#fig:006	 width=70%}

Потом я загрузил систему нажая Ctrl + x

Дальше я смотрел список файлов модулей, которые загружены
(рис. [-@fig:007	]).

		systemctl list-units

![список файлов модулей](image/07.png){#fig:007	 width=70%}




Потом я смотрел задействованные переменные среды оболочки
(рис. [-@fig:008	]).

		systemctl show-environment

![задействованные переменные среды](image/08.png){#fig:008	 width=70%}

Потом перезагрузил систему.
Затем при загрузке системы еще раз нажал esc и потом выбрал один ядер системы и нажал e чтобы открывать редактор, в котором добавил параметр systemd.unit=emergency.target и удалил rhgb и quiet
(рис. [-@fig:009	]).

		e
		systemd.unit=emergency.target

![редактор при загрузке](image/09.png){#fig:009	 width=70%}


Дальше я нажал Ctrl + X для продолжения загрузки

потом я еще раз посмотрел список всех загруженны файлов модулей (рис. [-@fig:010	]).

		systemctl list-units

![список всех загруженны файлов модулей](image/10.png){#fig:010	 width=70%}



Потом я еще раз перезагрузил систему через теминал
(рис. [-@fig:011	]).

		systemctl reboot

![reboot](image/11.png){#fig:011	 width=70%}



Еще раз при загрузке системы я еще раз входил в текстовой редактор и добавил другую строку чтобы загрузить систему в режиме редактора
(рис. [-@fig:013	]).


		rd.break


![настройка загрузки в режиме редактора](image/13.png){#fig:013	 width=70%}

Потом я нажал Ctrl + X  и продолжал загрузку



При загрузке ОС остановилась в момент загрузки initramfs и там я смог написать команду для монтирования корневой файловой системыв каталоге /. и тоже для создания содержимое каталога /sysimage 
(рис. [-@fig:014	]).

		mount -o remount,rw /sysroot
		chroot /sysroot

![монтирование и создание основных файлов](image/14.png){#fig:014	 width=70%}





Здесь я выполнил комнаду для изменения пароля и изменил пароль
(рис. [-@fig:015	]).

		passwd

![изменение пароля](image/15.png){#fig:015	 width=70%}



Потом я установил тип контекста для правильной работы системы в будущее время 
(рис. [-@fig:016	]).

		load_polici -i

![установка типа контекста](image/16.png){#fig:016	 width=70%}



Потом я вручную установил правильный тип контекста для /etc/shadow
(рис. [-@fig:017	]).

		chcon -t shadow_t /etc/shadow

![рисунка](image/17.png){#fig:017	 width=70%}

и перезагрузил систему 

		reboot -f









# Выводы

в эту лабораторную работу я смог смотреть как изменить параметры загрузки системы и как правильно сбросить пароль root

# Список литературы{.unnumbered}

::: {#refs}
:::
