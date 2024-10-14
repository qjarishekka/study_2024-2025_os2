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

Получить навыки работы с журналами мониторинга различных событий в системе.

# Задание

1. Продемонстрируйте навыки работы с журналом мониторинга событий в реальном
времени .
2. Продемонстрируйте навыки создания и настройки отдельного файла конфигурации
мониторинга отслеживания событий веб-службы.
3. Продемонстрируйте навыки работы с journalctl.
4. Продемонстрируйте навыки работы с journald.

# Выполнение лабораторной работы

Сначала я открыл 3 терминала под пользователя root  (рис. [-@fig:001]).

		su -
		

![терминалы](image/01.png){#fig:001 width=70%}


Потом во втором терминале я выполнил команду tail чтобы смотреть журнал в каталоге /var/log/messages (рис. [-@fig:002 ]).


		tail -f var/log/messages

![журнал каталога /var/log/messages](image/02.png){#fig:002    width=70%}


Дальше в третем терминале я вышел из режима администратора нажая клавиши Ctrl+d (рис. [-@fig:003  ]).

		Ctrl + d


![выход из режима администратора](image/03.png){#fig:003    width=70%}


Затем я попытался входить в режим суперпользователя но с неправильным паролем не удаваясь (рис. [-@fig:004  ]).
		
		su -
		asdfasdlkfj


![неправильный пароль](image/04.png){#fig:004    width=70%}


Потом я вернулся в первую вкладку и там я смог смотерть сообщение "Failed su (to root) username...."(рис. [-@fig:005  ]).

![сообщение о ошибке](image/05.png){#fig:005    width=70%}


Дальше я выполнил следующую комнаду (рис. [-@fig:006  ]):

		logger hello

![logger hello ](image/06.png){#fig:006    width=70%}

Тогда когда я вернулся во вторую вкладку там появились сообщение "hello" (рис. [-@fig:007  ]).


![сообщение hello](image/07.png){#fig:007    width=70%}

Потом я завершил просмотр журнала  (рис. [-@fig:008  ]).


		Ctrl + c

![завершение журнала ](image/08.png){#fig:008    width=70%}


Дальше я запустил мониторинг сообщений безопасности (рис. [-@fig:009  ]).

		tail -n 20 /var/log/secure

![мониторинг сообщений безопасности](image/09.png){#fig:009    width=70%}












(рис. [-@fig:00  ]).

![Название](image/placeimg_800_600_tech.png){#fig:00    width=70%}

# Выводы

После выполнения лабораторной работы я смог смотреть работу команд tail и journalctl чтобы смотреть журналы, которые сохраняют все выполнённые процессы и как настройт его.

# Список литературы{.unnumbered}

::: {#refs}
:::
