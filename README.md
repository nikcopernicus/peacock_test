# Тестовое задание

## Текст задание:

Создать Docker Compose скрипт для развертки кластера из трех инстансов cassandra, причем каждый из них должен быть доступен из основной (локальной) сети по отдельному ip адресу.

В ридми добавьте описание, все команды необходимые для запуска и скриншот результата.

Уточнение:
На машине А (ubuntu 22.04 lts) в локальной сети с ip 192.168.1.197 запускается скрипт docker-compose для поднятия 3 образов с ip адресами 192.168.1.200-202. Затем с машины Б (ubuntu 22.04 lts) из той же локальной сети с ip 192.168.1.198 необходимо подключиться через cqlsh к каждой из машин-образов. Все приведённые операции необходимо задокументировать и описать инструкцией с командами и объяснениями.

## Инструкция:

Для создания и поднятия машин A и B был использован VirtualBox

Ссылка на скачивание VirtualBox'a: https://www.virtualbox.org/wiki/Downloads

Создать машины uba и ubb (Ссылка на образ: https://ubuntu.com/download/desktop) Добавить обоим машинам адаптер сетвого моста в VirtualBox'е 

![image](https://github.com/nikcopernicus/peacock_test/assets/60931253/664947da-6033-46ec-a2a9-11a11c6773ef)

![image](https://github.com/nikcopernicus/peacock_test/assets/60931253/2ce7c7f7-58a4-4067-8c58-bdcbcccd543d)

1. На машине uba:
	- `sudo su`
	- `mkdir ~/tmp`
	- `cd ~/tmp`

	Установить докер:
	- `curl -fsSL https://get.docker.com -o install-docker.sh`
	- `sh install-docker.sh`

	Склонировать репозиотрий:
	- `git clone https://github.com/nikcopernicus/peacock_test`
	- `cd peacock_test`

	Настроить сеть через netplan:
	- `mv 99_config.yaml /etc/netplan/99_config.yaml`
	- `netplan apply`

	Развернуть кластер из трех инстансов cassandra:
	- `docker compose up -d`
1. На машине ubb:
	- `sudo su`
	- `mkdir ~/tmp`
	- `cd ~/tmp`

	Склонировать репозиотрий:
	- `git clone https://github.com/nikcopernicus/peacock_test`
	- `cd peacock_test`

	Настроить сеть через netplan:
	- `mv 98_config.yaml /etc/netplan/98_config.yaml`
	- `netplan apply`

	Установить cqlsh:
	- `snap install cqlsh`

	Подключиться через cqlsh к каждой из машин-образов:
	- `cqlsh 192.168.1.200`
    - `cqlsh 192.168.1.201`
    - `cqlsh 192.168.1.202`

## Результат
![image](https://github.com/nikcopernicus/peacock_test/assets/60931253/d0610425-f5c6-442a-b74c-ec634462aca3)

![image](https://github.com/nikcopernicus/peacock_test/assets/60931253/6e2f8792-d477-48b7-9f29-97b60a6bc9e4)


