---
## Front matter
lang: ru-RU
title: Презентация лабораторной работы №7
subtitle: Управление журналами событий в системе
author:
  - Кхари Жекка Кализая Арсе

## i18n babel
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

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
---


# Лабораторная работа 

# Последовательность выполнения работы


# Планирование задач с помощью cron

## статус демона crond


- su -
- systemctl status crond -l

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/02.png) 

:::
::::::::::::::


## настройка демона crond

- crontab -l  (для список заданий в расписании)
- crontab -e
- */1 * * * * logger This message is written from root cron
- crontab -l

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/06.png) 

:::
::::::::::::::



## журнал системных событий

- grep written /var/log/messages

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/08.png) 

:::
::::::::::::::


## изменеие расписания 

- crontab -e
- 0 */1 * * 1-5 logger This message is written from root cron


:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/09.png) 

:::
::::::::::::::


## настройка расписания по часам

- cd /etc/cron.hourly
- touch eachhour

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/12.png) 

:::
::::::::::::::


## настройка расписания по часам


- #!/bin/sh
- logger This message is written at $(date) 
- chmod +x eachhour

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/13.png) 

:::
::::::::::::::

## настройка расписания по часам

- cd /etc/cron.d
- touch eachhour
- 11 * * * * root logger This message is written from /etc/cron.d

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/16.png) 

:::
::::::::::::::


## проверка работы журнала 

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/17.png) 

:::
::::::::::::::


# Планирование заданий с помощью at


## служба atd

- su -
- systemctl status atd
- logger message from at 7:00
- Ctrl + d
- atq


:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/23.png) 

:::
::::::::::::::






