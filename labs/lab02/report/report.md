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

получить навыки о создании новых пользователей


# Задание

создать и переключиться к новым пользователим

# Теоретическое введение


Более подробно про Unix см. в [@tanenbaum_book_modern-os_ru; @robbins_book_bash_en; @zarrelli_book_mastering-bash_en; @newham_book_learning-bash_en].

# Выполнение лабораторной работы

Сначала я открил терминал и написал команду для посмотра настоящего пользователя (рис. [-@fig:001]).


![команада whoaim](image/1.jpg){#fig:001 width=70%}

Потом я вводил использовал команду id чтобы смотреть мой uid gid и к какой группе я принадлежу (рис. [-@fig:2  ]).

![команада id](image/2.jpg){#fig:002    width=70%}

Потом я переключил к учётной записи root (рис. [-@fig:3   ]).

![команада su](image/3.jpg){#fig:003    width=70%}

Потом я еще раз использовал команду id чтобы смотреть более информацию о пользователи (рис. [-@fig:4   ]).

![команада id в другом пользователе](image/4.jpg){#fig:004    width=70%}

Потом я использовал ту же команду su чтобы вернуться к учётной записи моего пользователя, в моем случае я написал su qjarishekka (рис. [-@fig:5   ]).

![вернуться к учётной записи](image/5.jpg){#fig:005    width=70%}

Дальше я написал sudo -i visudo и открился редактор текста файла /etc/sudoers (рис. [-@fig:6   ]).

![файл /etc/sudoers](image/6.jpg){#fig:006    width=70%}

Затем я открил тот же файл но запуская другой редактор, в этом случае mcedit. для етого я написал вариант предыдующей команды (рис. [-@fig:7   ]).

		sudo -i EDITOR=mcedit visudo


![файл /etc/sudoers на другом редакторе](image/7.jpg){#fig:007    width=70%}

Потом я искал строку %wheel ALL=(ALL) ALL (рис. [-@fig: 8  ]).

![поиск нужной строки](image/8.jpg){#fig:008    width=70%}


Дальше я создал новего пользователя alice в группе wheel (рис. [-@fig:9   ]).

		sudo -i useradd -G wheel alicе
		
![новый пользователь alice](image/9.jpg){#fig:009    width=70%}

и убедился что пользователь alice добавлен в группу wheel с помощью команды id alice (рис. [-@fig:10   ]). 

![id alice](image/10.jpg){#fig:010    width=70%}

После того как я создал пользователя alice я дал ей новый пароль с следующей командой (рис. [-@fig:11   ]).

		sudo -i passwd alice

![пароль для пользователя alice](image/11.jpg){#fig:011    width=70%}

этому паролю надо было ввести дважды


Потом я переключился на уётную запись alice (рис. [-@fig:12   ]).

		su alice

![su alice](image/12.jpg){#fig:012    width=70%}

Потом я создал другого пользователя bob (рис. [-@fig:13   ]).

		sudo useradd bob

![новый пользователь bob](image/13.jpg){#fig:013    width=70%}

Дальше я проверал что пользователь создан с помощью команды id (рис. [-@fig:14   ]).

id bob

![проверка создания пользователя](image/14.jpg){#fig:014  width=70%}

потом я установил пароль для bob (рис. [-@fig:15   ]).

		sudo passwd bob


![пароль для boba](image/15.jpg){#fig:015    width=70%}











(рис. [-@fig:   ]).

![Название рисунка](image/placeimg_800_600_tech.jpg){#fig:0    width=70%}

# Выводы

Здесь кратко описываются итоги проделанной работы.

# Список литературы{.unnumbered}

::: {#refs}
:::
