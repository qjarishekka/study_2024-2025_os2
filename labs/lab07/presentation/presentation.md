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

## Последовательность выполнения работы

## Мониторинг журнала системных событий в реальном времени

- su -
- tail -f /var/log/messages
- logger hello
- su -

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/07.png) 

:::
::::::::::::::


# изменение правил rsyslog.conf

## проверка работы rsyslog

- dnf -y install httpd
- systemctl start httpd
- systemctl enable httpd
- tail -f /var/log/httpd/error_log

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/12.png) 

:::
::::::::::::::


## настройка правил rsyslog.conf для веб-службы

- в файле /etc/httpd/conf/httpd.conf
- добавил строку: Error syslog:local1
- в созданном файле /etc/rsyslog.d/httpd.conf
- написал local1.* -/var/log/httpd-error.log


:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/14.png) 

:::
::::::::::::::


## перезагруска веб-службы 

- systemctl restart rsyslog.service
- systemctl restart httpd

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/17.png) 

:::
::::::::::::::


## настройка отладочной информации 

- cd /etc/rsyslog.d
- touch debug.conf
- echo "*debug /var/log/messages-debug" > /etc/rsyslog.d/debug.conf

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/19.png) 

:::
::::::::::::::


## работы отладки

- tail -f /var/log/messages-debug
- logger -p daemon.debug "Daemon Debug Message"

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/23.png) 

:::
::::::::::::::


# Использование journalctl

## журнал

- journalctl

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/25.png) 

:::
::::::::::::::


## журнал без использования пейджера

- journalctl --no-pager

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/28.png) 

:::
::::::::::::::

## журнал в реальном времени

- journalctl -f

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/29.png) 

:::
::::::::::::::

## журнал событий для UID0

- journalctl _UID=0


:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/31.png) 

:::
::::::::::::::

## отображение последных 2- строк журнала

- journalctl -n 20

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/32.png) 

:::
::::::::::::::


## сообщения об ошибах 

- journalctl -p err

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/33.png) 

:::
::::::::::::::

## по времени

- journalctl --since yesterday

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/34.png) 

:::
::::::::::::::

## по времени

- journalctl --since yesterday -p err

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/35.png) 

:::
::::::::::::::

## детальная информация 

- journalctl -o verbose

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/36.png) 

:::
::::::::::::::


## дополнительная информация

- journalctl _SYSTEM_UNIT=sshd.service


:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/37.png) 

:::
::::::::::::::



# Постоянный журнал journald

## создание журнала

- mkdir -p /var/log/journal
- chown root:systemd -journal /var/log/journal
- chmod 2755 /var/log/jorunal
- killall -USR1 systemd-journald


:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/42.png) 

:::
::::::::::::::


## Проверка журнала

- journalctl -b

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/43.png) 

:::
::::::::::::::






