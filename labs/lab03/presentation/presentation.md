---
## Front matter
lang: ru-RU
title: Лабораторная работа №3
subtitle: настройка прав доступа
author:
  - Кхари жекка кализая арсе
institute:
  - Российский университет дружбы народов, Москва, Россия
  - Объединённый институт ядерных исследований, Дубна, Россия
date: 01 января 1970

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

# ЦЕЛЬ РАБОТЫ

## Цель работы

- Получить навыки о настройке прав доступа для разных пользователей в разных каталогов и файлов


# Управление базовыми разрешениями

# терминал под пользователем root

## команда su

![](./image/1.png)

# изменение владелцев каталогов

## комнада chgrp

![](./image/5.png)

# настройка разрешений 

## команда chmod

![](./image/6.png)

## команда chmod

![](./image/7.png)


# терминал под пользователем bob

## Проверка разрешений доступа

![](./image/10.png)


# Управление специальными разрешениями

# терминал под пользователем alice

## создание файлов

![](./image/13.png)


# терминал под пользователем bob

## удаление файлов пользователя alice 

![](./image/17.png)


## новые защищенные файлы

![](./image/18.png)

## новые защищенные файлы

![](./image/19.png)


## новые созданные файлы пользователем alice


![](./image/20.png)


## Показ атрибута sticky bit


![](./image/21.png)



# Управление расширенными разрешениями с использованием списков ACL

## Команада setfacl

![](./image/22.png)


## команада getfacl 

![](./image/23.png)




## создание примерный файл

![](./image/25.png)



## установление ACL


![](./image/30.png)


# Проверка работы ACL

![](./image/35.png)


# Результаты

- используя команду chgrp изменить группу владелцев можно
- chmod изпользуется чтобы дать права доступа
- sticky bit защищает файлы от изменений другими пользователями 
- setfacl даёт специяльные права доступа




