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


Дальше я начал другую часть лабораторной работы.

Сначала я установил утилит httpd (рис. [-@fig:010  ]).

		dnf -y install httpd

![установка httpd](image/10.png){#fig:010    width=70%}

Потом я инициализировал его (рис. [-@fig:011  ]).

		systemctl start httpd
		systemctl enable httpd


![запуск утилита](image/11.png){#fig:011    width=70%}

Потом во второй вкладке терминала я смотрел журнал сообщений об ошибах веб-службы (рис. [-@fig:012  ]).

		tail -f /var/log/httpd/error_log
		
![журнал сообщений об ошибах](image/12.png){#fig:012    width=70%}


Потом я перешел в третьюю вкладку и получил полномочия администратора (рис. [-@fig:013  ]). и в файле /etc/httpd/conf/httpd.conf я добавил одну строку (рис. [-@fig:014  ]).

		su -
		vim /etc/httpd/conf/httpd.conf
		Errorlog syslog:local1
		:wq


![пользователь root](image/13.png){#fig:013    width=70%}


![изменение файла /etc/httpd/conf/httpd.conf](image/14.png){#fig:014    width=70%}

Потом я перешел в друкой каталог /etc/rsyslog.d и создал один файл "httpd.conf" (рис. [-@fig:015  ]).

		cd /etc/rsyslog.d
		touch httpd.conf
		
![httpd.conf](image/15.png){#fig:015    width=70%}

В этом файле я добавил одну строку и сохранил его (рис. [-@fig:016  ]).
		
		mcedit httpd.conf
		local1.* -/var/log/httpd-error.log
		
		f10

![новая строка](image/16.png){#fig:016    width=70%}


Дальше я перешел в первую вкладку терминала и перезагрузил конфигурацию rsyslogd и веб-службу (рис. [-@fig:017  ]).

		systemctl restart rssyslog.service
		systemctl restart httpd

![перезагрузка конфигурацию rsyslogd и веб-службу](image/17.png){#fig:017    width=70%}


Затем я перешел в третьюю вкладку и создал отдельный файл конфигурации для мониторинга отладочной информации (рис. [-@fig:019  ]).

		cd /etc/rsyslog.d
		touch debug.conf
		echo "*.debug /var/log/messages-debug" > /etc/rsyslog.d/debug.conf

![конфигурация для мониторинга отладочной информации](image/19.png){#fig:019    width=70%}


Потом еще раз в первой вкладке терминала снова перезапустил rsyslogd (рис. [-@fig:020 ]).

		systemctl restart rsyslog.service

![перезапуск rsyslogd](image/20.png){#fig:020    width=70%}

Затем во второй вкадке терминала я запустил мониторинг отладочной информации (рис. [-@fig:021  ]).

		tail -f /var/log/messages-debug

![мониторинг отладочной информации ](image/21.png){#fig:021    width=70%}


Потом я в третьей вкладке терминала выполнил команду logger  (рис. [-@fig:022  ]).

		logger -p daemon.debug "Daemon Debug Message

![logger ](image/22.png){#fig:022    width=70%}


Затем я закрыл трассиворку файла журнала во второй вкладке (рис. [-@fig:024  ]).

		Ctrl + c

![закрытие трассироваки файла журнала ](image/24.png){#fig:024    width=70%}


Потом я начал следующую часть лабораторной работы (Использование journalctl)

Сначала во второй вкладке терминала я посмотрел содержимое журнала с событиями с момента последнего запуска системы (рис. [-@fig:025  ]).

		journalctl

![журнал ](image/25.png){#fig:025    width=70%}

Потом я делал нескольки действие там (enter и q) (рис. [-@fig:026  ] и рис. [-@fig:027  ]).

		enter
		q



![enter](image/26.png){#fig:026    width=70%}

![q](image/27.png){#fig:027   width=70%}


Потом я выполнил одну команду чтобы смотреть содержимое журнала без использования пейджера (рис. [-@fig:028  ]).

		journalctl --no-pager

![журнал без изпользования пейджера](image/28.png){#fig:028    width=70%}

Потом я запускал журнал в режиме просмотра в реальном времени (рис. [-@fig:029  ]).

		journalctl -f

![журнал в режиме реального времени](image/29.png){#fig:029    width=70%}


Потом я закрыл журнал нажая клавиши Ctrl + c (рис. [-@fig:030  ]).

		Ctrl + c

![Закрытие журнала](image/30.png){#fig:030    width=70%}


Потом я смотрел события для UID0  (рис. [-@fig:031  ]).

		journalctl _UID=0

![журнал событий для UID0](image/31.png){#fig:031    width=70%}


Дальше я смотрел события для отображения последниз 20 строк журнала (рис. [-@fig:032  ]).

		journalctl -n 20

![журнал событий для отображения последний 20 строк](image/32.png){#fig:032    width=70%}


и для просмотра только сообщений об ошибах (рис. [-@fig:033  ]).

		journalctl -p err

![журнал событий для отображения ошибках](image/33.png){#fig:033    width=70%}


Потом я упорядочил журнал по дате (рис. [-@fig:034  ]).

		journalctl --since yesterday

![данные журнала со вчерашнего дня](image/34.png){#fig:034    width=70%}


Потом только ошибки с вчерашнего дня (рис. [-@fig:035  ]).

		journalctl --since yesterday -p err

![данные журнала об ошибках со вчерашнего дня](image/35.png){#fig:035    width=70%}

для детальной информации я использовал следующую команду  (рис. [-@fig:036  ]).

		journalctl -o verbose

![журнал с детальной информацией](image/36.png){#fig:036    width=70%}


и для просмотра дополнительной информации я написал следующую команду (рис. [-@fig:037  ]).

		journalctl _SYSTEMD_UNIT-sshd.service
 
![дополнительная информация в журнале](image/37.png){#fig:037    width=70%}



Потом я начал следующую часть (Постоянный журнал journald)

Сначала я создал новый каталог journal (рис. [-@fig:039  ]).

		mkdir -p /var/log/journal

![новый каталог journal](image/39.png){#fig:039    width=70%}


Потом я изменил праву доступа для каталога journal чтобы смог записывать в него информацию (рис. [-@fig:041  ]).

		chown root:systemd-journal /var/log/journal
		
![измение прав доступа каталога journal](image/41.png){#fig:041    width=70%}

Потом чтобы принимать все действия я перезапустил службу systemd-journald (рис. [-@fig:042  ]).

		killall -USR1 systemd-journald

![перезапуск службы systemd-journald](image/42.png){#fig:042   width=70%}


Теперь systemd постоянный и чтобы смотреть сообщения журнала с момента последный перезагрузки я ввел последную команду  (рис. [-@fig:043  ]).


![сообщения в журнале](image/43.png){#fig:043    width=70%}









# Выводы

После выполнения лабораторной работы я смог смотреть работу команд tail и journalctl чтобы смотреть журналы, которые сохраняют все сообщения выполнений команд или других действий и как настройт его.

# Список литературы{.unnumbered}

::: {#refs}
:::
