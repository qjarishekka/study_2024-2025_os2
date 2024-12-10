---
## Front matter
lang: ru-RU
title: Презентация лабораторной работы №15
subtitle: Управление логическими томами
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

# Создание физического тома

- цель: создать физического тома


## удаление партиций

- Команды:
   - vim /etc/fstab
   - (коментировать строку)
   - umount /mnt/data
   - fdisk
   - o ENTER w ENTER
   - partprobe /dev/sdb

## удаление партиций

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/01.png) 

:::
::::::::::::::

## удаление партиций

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/04.png) 

:::
::::::::::::::

# создание физического тома

## создание физического тома

- команды:
   - fdisk /dev/sdb 
   - n p (по умолчанию) t 8e w
   - partprobe /dev/sdb
   - pvcreate /dev/sdb1
   - pvs

## создание физического тома


:::::::::::::: {.columns align=center}
::: {.column width="70%"}

![](./image/2.png) 

:::
::::::::::::::


