---
## Front matter
lang: ru-RU
title: Прецентация лабораторной работы № 4.
subtitle: Работа с программными пакетами
author:
  - Кхари Жекка Кализая Арсе.
institute:
  - Российский университет дружбы народов, Москва, Россия

date: 28 сентябра 2024

## i18n babel
babel-lang: russian
babel-otherlangs: english

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

# Последовательность выполнения работы

# Работа с репозиториями

## консоль под пользователя root

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/1.png) 

:::
::::::::::::::

## содержание файлов .repos

- cd /etc/yum.repos.d
- ls
- cat название_репозитория.repo

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/2-1.png)

:::
::::::::::::::

## список репозиториев

- dnf repolist

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/3.png)

:::
::::::::::::::

## список пакетов "user"

- dnf search user

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/4.png)

:::
::::::::::::::


## установка nmap

- dnf search nmap
- dnf info nmap
- dnf install nmap
- dnf install nmap\*

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/5-3.png)

:::
::::::::::::::

## удаление nmap

- dnf remove nmap
- dnf remove nmap\*

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/6-2.png)

:::
::::::::::::::


## RPM Development Tools

- dnf groups list
- LANG=C dnf groups list
- dnf groups info "RPM Development Tools"
- dnf groupinstall "RPM Development Tools"


:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/7-4.png)

:::
::::::::::::::



## удаление RPM Development Tools

- dnf groupremove "RPM Development Tools"

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/7-6.png)

:::
::::::::::::::

## история команды dnf

- dnf history

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/8-1.png)

:::
::::::::::::::

# Использование rpm


## загрузка пакета lynx

- dnf list lynx
- dnf install lynx --downloadonly

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/9-3.png)

:::
::::::::::::::

## пойск пакета lynx

- find /var/cache/dnf/ -name lynx*

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/10.png)

:::
::::::::::::::

## установка пакета lynx

- rpm -Uhv lynx-2.8.9-20.el9.x86_64.rpm

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/11.png)

:::
::::::::::::::




## расположение исполняемого файла

- which lynx

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/12.png)

:::
::::::::::::::

## к какому пакету принадлежит lynx? 

- rpm -qf $(which lynx)
- rpm -qi lynx		(для дополнительной иформации)

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/14.png)

:::
::::::::::::::


## Список всех файлов в пакете
- rpm -ql lynx

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/15.png)

:::
::::::::::::::



## документация

- rpm -qd lynx

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/16.png)

:::
::::::::::::::

## конфигурация

- rpm -qc lynx

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/17.png)

:::
::::::::::::::


## скрипты 

- rpm -q --scripts lynx

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/18.png)

:::
::::::::::::::


## запуск lynx

- lynx 


:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/19.png)

:::
::::::::::::::

## удаление пакета

- rpm -e lynx
- ls

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/20.png)

:::
::::::::::::::


# Примерная ситуация для показа работы rpm



## загрузка пакета dnsmasq


- dnf list dnsmasq
- dnf install dnsmasq


:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/21-2.png)

:::
::::::::::::::

## расположение исполняемого файла


- which dnsmasq


:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/21-3.png)

:::
::::::::::::::


## файл содержащий пакет dnsmasq
- rpm -qf $(which dnsmasq)



:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/22-1.png)

:::
::::::::::::::

## дополнительная информация 

- rpm -qi dnsmasq


:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/22-2.png)

:::
::::::::::::::


## писок всех файлов в пакете 


- rpm -ql dnsmasq


:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/23-1.png)

:::
::::::::::::::

## документация 

- rpm -qd dnsmasq


:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/23-2.png)

:::
::::::::::::::


## конфигурационные файлы

- rpm -qc dnsmasq

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/24.png)

:::
::::::::::::::

## скрипты 

- rpm -q --scripts dnsmasq


:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/25.png)

:::
::::::::::::::


## удаление пакета 


- rpm -e dnsmask

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

![](./image/26.png)

:::
::::::::::::::




