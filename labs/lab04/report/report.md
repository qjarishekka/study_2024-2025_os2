---
## Front matter
title: "Шаблон отчёта по лабораторной работе №4"
subtitle: "Работа с программными пакетами"
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

Сначала, я открыл терминал и перешел в режим работы суперпользователя (рис. [-@fig:001     ]).
		
		-su

![запуск терминала](image/1.png){#fig:001    width=70%}

Потом я перешел в каталог /etc/yum.repos.d и читал все файлы с именами repos ( от рис. [-@fig:002-1     ] до рис. [-@fig:002-4 ]).

		cd /etc/yum.repos.d
		ls
		cat название_репозитория.repo


![rocky-addons.repo](image/2-1.png){#fig:002-1    width=70%}

![rocky-devel.repo ](image/2-2.png){#fig:002-2    width=70%}

![rocky-extras.repo](image/2-3.png){#fig:002-3    width=70%}

![ rocky.repo](image/2-4.png){#fig:002-4    width=70%}

Дальше я смотрел список репозиториев  (рис. [-@fig:003     ]).

		dnf search user

![список репозиториев](image/3.png){#fig:003    width=70%}



Потом я установил nmap ( от рис. [-@fig:005-1     ]  до рис. [-@fig:005-4     ]).

		dnf search nmap
		dnf info nmap
		dnf install nmap
		dnf install nmap\*


![dnf search nmap](image/5-1.png){#fig:005-1    width=70%}

![dnf info nmap](image/5-2.png){#fig:005-2    width=70%}

![dnf install nmap](image/5-3.png){#fig:005-3    width=70%}

![dnf install nmap\*](image/5-4.png){#fig:005-4    width=70%}

команды dnf install nmap\* и dnf install nmap отличаются в чем, что первый устанавливает все пакеты у которых есть nmap в имени, а второй только тот пакет, которым называется nmap


Потом я удалил nmap  ( от рис. [-@fig:006-1     ] до [-@fig:006-4     ] ).

		dnf remove nmap
		dnf remove nmap\*
		
![удаление nmap](image/6-1.png){#fig:006-1    width=70%}

![удаление nmap](image/6-2.png){#fig:006-2    width=70%}

![удаление nmap](image/6-3.png){#fig:006-3    width=70%}

![удаление nmap](image/6-4.png){#fig:006-4  width=70%}


Потом я получил список имеющихся групп пакетов и установил группу пакетов RPM Development tools  (от рис. [-@fig:007-1     ] до рис. [-@fig:007-5     ]).

		dnf groups list
		LANG=C dnf groups list
		dnf groups info "RPM Development Tools"
		dnf groupinstall "RPM Development Tools"
		
![dnf groups list](image/7-1.png){#fig:007-1    width=70%}

![LANG=C dnf groups list](image/7-2.png){#fig:007-2    width=70%}

![dnf groups info "RPM Development Tools"](image/7-3.png){#fig:007-3    width=70%}

![dnf groupinstall "RPM Development Tools"](image/7-4.png){#fig:007-4    width=70%}

![подтверждение установки](image/7-5.png){#fig:007-5    width=70%}

Потом я удалил RPM Developments Tools (рис. [-@fig:007-6     ]).

		dnf groupremove "RPM Development Tools"

![удаление RPM Developments Tools](image/7-6.png){#fig:007-6    width=70%}
		
		
		
Потом я смотрел историю команд  (рис. [-@fig:008-1     ]).

		dnf history

![история команд](image/8-1.png){#fig:008-1    width=70%}


Затем выполнил следующую команду  (рис. [-@fig:008-2     ]).

		dnf history undo 6

![undo](image/8-2.png){#fig:008-2    width=70%}


Потом я установил текстовый браузер lynx (рис. [-@fig:009-1     ] - рис. [-@fig:009-3     ]).



		dnf list lynx
		dnf install lynx --downloadonly

![поиск пакета](image/9-1.png){#fig:009-1    width=70%}

![загрузка lynx](image/9-2.png){#fig:009-2    width=70%}

![подтверждение загрузки](image/9-3.png){#fig:009-3    width=70%}


Потом я искал загруженный пакет  (рис. [-@fig:010     ]).

		find /var/cache/dnf/ -name lynx*

![поиск пакета](image/10.png){#fig:010    width=70%}

Затем я установил пакет lynx (рис. [-@fig:011     ]).

		rpm -Uhv lynx-2.8.9-20.el9.x86_64.rpm

![установление пакета](image/11.png){#fig:011    width=70%}

Потом я определил расположение исполняемого файла lynx (рис. [-@fig:012     ]).

		which lynx

![расположение исполняемого файла](image/12.png){#fig:012   width=70%}

Потом я определил по имени файла, к какому пакету принадлежит lynx  (рис. [-@fig:013     ]).


		rpm -qf $(which lynx)

![lynx](image/13.png){#fig:013    width=70%}

и чтобы смотрет дополнительную информацию (рис. [-@fig:014     ]) я введил команду  : 



![дополнительная информация](image/14.png){#fig:014    width=70%}

Потом чтобы получил список всех файлов в пакете я использовал опцию -ql  (рис. [-@fig:015     ]).

		rpm -ql lynx

![список файлов пакета](image/15.png){#fig:015    width=70%}


Также я получил перечень файлов с документацей пакета с помощью опции -qd (рис. [-@fig:016     ]).

		rpm -qd lynx

![документация пакета](image/16.png){#fig:016    width=70%}


Чтобы смотреть конфигурацию пакета я исползовал опцию -qc  (рис. [-@fig:017     ]).

		rpm -qc lynx

![конфигурация пакета](image/17.png){#fig:017    width=70%}


Потом я получил расположение и содержание скриптов с помощью опции -q --scripts (рис. [-@fig:018     ]).

		rpm -q --scripts lynx

![скрипты пакета ](image/18.png){#fig:018    width=70%}

в моем случае не былы скрипты


Потом я открыл другой терминал и запускал lynx (рис. [-@fig:019     ]).

		lynx

![запуск lynx](image/19.png){#fig:019    width=70%}


Потом я вернулся в предыдующий терминал и удалил lynx (рис. [-@fig:020     ]).


		rpm -e lynx
		ls

![удаление lynx](image/20.png){#fig:020    width=70%}


Потом я начал установить пакет dnsmasq. для этого я выполнил 2 команду (рис. [-@fig:021     ]).

		dnf list dnsmasq
		dnf install dnsmasq

![установка пакета](image/21-2.png){#fig:021    width=70%}

Потом я определил расположение пакета (рис. [-@fig:021-3     ]).

		which dnsmasq

![расположение пакета](image/21-3.png){#fig:021-3    width=70%}


Потом я опеределил к какому пакету принадлежит dnsmasq (рис. [-@fig:022-1     ]).

		rpm -qf $(which dnsmasq)

![dnsmasq](image/22-1.png){#fig:022-1    width=70%}


Дальше я получил дополнительную информацию (рис. [-@fig:022-2     ]).

		rpm -qi dnsmasq

![информация пакета](image/22-2.png){#fig:022-2    width=70%}




Потом я получил список всех файлов в пакете (рис. [-@fig:023-1     ]).

		rpm -ql dnsmasq

![список файлов](image/23-1.png){#fig:023-1    width=70%}

и также я получил перечень файлов с документацией пакета (рис. [-@fig:023-2     ]).

		rpm -qd dnsmasq

![перечень файлов с документацией](image/23-2.png){#fig:023-2    width=70%}


Потом я смотрел перечень и месторасположение конфигурационных файлов пакета (рис. [-@fig:024     ]).

		rpm -qc dnsmasq

![месторасположение конфигурационных файлов пакета](image/24.png){#fig:024    width=70%}


Дальше я определил расположение и содержание скриптов пакета (рис. [-@fig:025     ]).

		rpm -q --scripts dnsmasq

![расположение скриптов](image/25.png){#fig:025    width=70%}

Они используются чтобы установить дополнительные пакеты при определенных случаях

Дальше я удалил пакет  (рис. [-@fig:026     ]).

		rpm -e dnsmask

![удаление пакета](image/26.png){#fig:026    width=70%}

Контрольные вопросы


1. Какая команда позволяет вам искать пакет rpm, содержащий файл useradd?
2. Какие команды вам нужно использовать, чтобы показать имя группы dnf, которая
содержит инструменты безопасности и показывает, что находится в этой группе?
3. Какая команда позволяет вам установить rpm, который вы загрузили из Интернета
и который не находится в репозиториях?
4. Вы хотите убедиться, что пакет rpm, который вы загрузили, не содержит никакого
опасного кода сценария. Какая команда позволяет это сделать?
5. Какая команда показывает всю документацию в rpm?
6. Какая команда показывает, какому пакету rpm принадлежит файл?
При ответах на контрольные вопросы рекомендуется ознакомиться с информацией
из [1—4].




# Выводы

В этой лабораторной работе я изучал работу с программными пакетами и менеджерами пакетов, я смотрел функцию утилита dnf и их опции для загрузки установке и удаления пакетов и их соответственых скриптов.




# Список литературы{.unnumbered}

::: {#refs}
:::
