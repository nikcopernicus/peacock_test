# Тестовое задание

## Текст задание:

Создать Docker Compose скрипт для развертки кластера из трех инстансов cassandra, причем каждый из них должен быть доступен из основной (локальной) сети по отдельному ip адресу.

В ридми добавьте описание, все команды необходимые для запуска и скриншот результата.

Уточнение:
На машине А (ubuntu 22.04 lts) в локальной сети с ip 192.168.1.197 запускается скрипт docker-compose для поднятия 3 образов с ip адресами 192.168.1.200-202. Затем с машины Б (ubuntu 22.04 lts) из той же локальной сети с ip 192.168.1.198 необходимо подключиться через cqlsh к каждой из машин-образов. Все приведённые операции необходимо задокументировать и описать инструкцией с командами и объяснениями.

## Инструкция:

Для создания и поднятия машин A и B были использованы Vagrant и VirtualBox

Ссылка на скачивание Vagrant'a: https://disk.yandex.ru/d/7QA07XvEi5QqcQ
Ссылка на скачивание VirtualBox'a: https://www.virtualbox.org/wiki/Downloads

1. Склонировать репозиторий: `git clone https://github.com/nikcopernicus/peacock_test.git`
1. Перейти в каталог: `cd peacock_test`
1. Инициализировать текущий каталог как среду Vagrant: `vagrant init`
1. Скачать vagrant box в текущий каталог: https://app.vagrantup.com/ubuntu/boxes/jammy64/versions/20230805.0.0/providers/virtualbox.box
1. Добавить vagrant box `vagrant box add ubuntu/jammy64 jammy-server-cloudimg-amd64-vagrant.box` 
1. Поднять машины A и B: `vagrant up`
1. Подключиться к машине B: `vagrant ssh ubb`
1. Подключиться через cqlsh к каждой из машин-образов на машине A: 
    - `cqlsh 192.168.1.200`
    - `cqlsh 192.168.1.201`
    - `cqlsh 192.168.1.202`

## Результат
![изображение](https://github.com/nikcopernicus/peacock_test/assets/60931253/ca2c2e0b-2a2a-40fa-8181-b681c61c7fa9)
