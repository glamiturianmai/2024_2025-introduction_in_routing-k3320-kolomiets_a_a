University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Introduction in routing](https://github.com/itmo-ict-faculty/introduction-in-routing)

Year: 2024/2025

Group: K3320

Author: Kolomiets Alice Denisovna

Lab: Lab3

Date of create: 04.11.2024

Date of finished: 05.11.2024

# Отчёт по лабораторной работе №3 "Эмуляция распределенной корпоративной сети связи, настройка OSPF и MPLS, организация первого EoMPLS"

***Цель:*** Изучить протоколы OSPF и MPLS, механизмы организации EoMPLS.


## Ход работы

### Схема работы: 

<img src="./images/schema.png" style="width:500px; height: auto; background: white">

### RO1.NY:
<img src="./images/NY.png" style="display: block;width:500px; height: auto; background: white; margin-bottom: 10px">

### RO1.LND:
<img src="./images/LDN.png" style="display: block;width:500px; height: auto; background: white; margin-bottom: 10px">

### RO1.HKI:
<img src="./images/HKI.png" style="display: block;width:500px; height: auto; background: white; margin-bottom: 10px">

### RO1.SPB:
<img src="./images/SPB.png" style="display: block;width:500px; height: auto; background: white; margin-bottom: 10px">

### RO1.MSC:
<img src="./images/MSK.png" style="display: block;width:500px; height: auto; background: white; margin-bottom: 10px">

### RO1.LBN:
<img src="./images/LBN.png" style="display: block;width:500px; height: auto; background: white; margin-bottom: 10px">

## Результаты пингов (PC1 -> SGI_PRISM, SGI_PRISM -> PC1)
<img src="./images/ping1.png" style="display: block;width:500px; height: auto; background: white; margin-bottom: 10px">
<img src="./images/ping2.png" style="display: block;width:500px; height: auto; background: white; margin-bottom: 10px">

##  Трассировка между роутерами (SPB и NY) - можно увидеть что используются разные маршруты 
<img src="./images/traceroute.png" style="display: block;width:500px; height: auto; background: white; margin-bottom: 10px">
