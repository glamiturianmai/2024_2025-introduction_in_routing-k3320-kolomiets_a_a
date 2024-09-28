University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Introduction in routing](https://github.com/itmo-ict-faculty/introduction-in-routing)

Year: 2024/2025

Group: K3320

Author: Kolomiets Alice Denisovna

Lab: Lab1

Date of create: 21.09.2024

Date of finished: 28.09.2024

# Отчёт по лабораторной работе №1 "Установка ContainerLab и развертывание тестовой сети связи"

***Цель:*** ознакомиться с инструментом ContainerLab и методами работы с ним, изучить работу VLAN, IP адресации и т.д.


## Ход работы

Сначала была попытка сделать лабораторную работу в виртуальной машине (Ubuntu) но после сложностей с развертыванием контейнером и подключения к устройствам было принято решение установит Linux второй ОС. После этого все было реализовано успешно 


В yaml-файле была задана топология сети, указанная на схеме

<img src="./imgs/1.png" style="width:500px; height: auto; background: white">

## Конфигурация
<img src="./imgs/RO1-config.jpg" style="display: block;width:500px; height: auto; background: white; margin-bottom: 10px">
<img src="./imgs/SWO1-config.jpg" style="display: block;width:500px; height: auto; background: white; margin-bottom: 10px">
<img src="./imgs/SWO2.01-config.jpg" style="display: block;width:500px; height: auto; background: white; margin-bottom: 10px">
<img src="./imgs/SWO2.02-config.jpg" style="display: block;width:500px; height: auto; background: white; margin-bottom: 10px">
### После задания конфигураций нод, проверим работоспособность:

<img src="./imgs/SWO1.jpg" style="display: block;width:500px; height: auto; background: white; margin-bottom: 10px">
<img src="./imgs/SWO2.01.jpg" style="display: block;width:500px; height: auto; background: white; margin-bottom: 10px">
<img src="./imgs/SWO2.02.jpg" style="display: block;width:500px; height: auto; background: white; margin-bottom: 10px">