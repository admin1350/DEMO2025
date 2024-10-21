# DEMO2025

## 1. Произведите базовую настройку устройств

  ● Настройте имена устройств согласно топологии. Используйте
полное доменное имя  
  ● На всех устройствах необходимо сконфигурировать IPv4
  ● IP-адрес должен быть из приватного диапазона, в случае, если сеть
локальная, согласно RFC1918
  ● Локальная сеть в сторону HQ-SRV(VLAN100) должна вмещать не
более 64 адресов
  ● Локальная сеть в сторону HQ-CLI(VLAN200) должна вмещать не
более 16 адресов
  ● Локальная сеть в сторону BR-SRV должна вмещать не более 32
адресов
  ● Локальная сеть для управления(VLAN999) должна вмещать не
более 8 адресов
  ● Сведения об адресах занесите в отчёт, в качестве примера
используйте Таблицу 3
## 2. Настройка ISP
  ● Настройте адресацию на интерфейсах:
    o Интерфейс, подключенный к магистральному провайдеру, получает адрес по DHCP
38
    o Настройте маршруты по умолчанию там, где это необходимо
    o Интерфейс, к которому подключен HQ-RTR, подключен к сети 172.16.4.0/28
    o Интерфейс, к которому подключен BR-RTR, подключен к сети 172.16.5.0/28
    o На ISP настройте динамическую сетевую трансляцию в сторону HQ-RTR и BR-RTR для доступа к сети Интернет
## 3. Создание локальных учетных записей
● Создайте пользователя sshuser на серверах HQ-SRV и BR-SRV
o Пароль пользователя sshuser с паролем P@ssw0rd
o Идентификатор пользователя 1010
o Пользователь sshuser должен иметь возможность запускать sudo
без дополнительной аутентификации.
● Создайте пользователя net_admin на маршрутизаторах HQ-RTR и
BR-RTR
o Пароль пользователя net_admin с паролем P@$$word
o При настройке на EcoRouter пользователь net_admin должен
обладать максимальными привилегиями
o При настройке ОС на базе Linux, запускать sudo без
дополнительной аутентификации
## 4. Настройте на интерфейсе HQ-RTR в сторону офиса HQ виртуальный
коммутатор:
● Сервер HQ-SRV должен находиться в ID VLAN 100
● Клиент HQ-CLI в ID VLAN 200
● Создайте подсеть управления с ID VLAN 999
● Основные сведения о настройке коммутатора и выбора реализации
разделения на VLAN занесите в отчёт
## 5. Настройка безопасного удаленного доступа на серверах HQ-SRV и BR-
SRV:
39
● Для подключения используйте порт 2024
● Разрешите подключения только пользователю sshuser
● Ограничьте количество попыток входа до двух
● Настройте баннер «Authorized access only»
## 6. Между офисами HQ и BR необходимо сконфигурировать ip туннель
 Сведения о туннеле занесите в отчёт
 На выбор технологии GRE или IP in IP
## 7. Обеспечьте динамическую маршрутизацию: ресурсы одного офиса
должны быть доступны из другого офиса. Для обеспечения динамической
маршрутизации используйте link state протокол на ваше усмотрение.
● Разрешите выбранный протокол только на интерфейсах в ip
туннеле
● Маршрутизаторы должны делиться маршрутами только друг с
другом
● Обеспечьте защиту выбранного протокола посредством
парольной защиты
● Сведения о настройке и защите протокола занесите в отчёт
## 8. Настройка динамической трансляции адресов.
● Настройте динамическую трансляцию адресов для обоих офисов.
● Все устройства в офисах должны иметь доступ к сети Интернет
## 9. Настройка протокола динамической конфигурации хостов.
● Настройте нужную подсеть
● Для офиса HQ в качестве сервера DHCP выступает маршрутизатор
HQ-RTR.
● Клиентом является машина HQ-CLI.
● Исключите из выдачи адрес маршрутизатора
● Адрес шлюза по умолчанию – адрес маршрутизатора HQ-RTR.
● Адрес DNS-сервера для машины HQ-CLI – адрес сервера HQ-SRV.
● DNS-суффикс для офисов HQ – au-team.irpo
40
● Сведения о настройке протокола занесите в отчёт
## 10. Настройка DNS для офисов HQ и BR.
● Основной DNS-сервер реализован на HQ-SRV.
● Сервер должен обеспечивать разрешение имён в сетевые адреса
устройств и обратно в соответствии с таблицей 2
● В качестве DNS сервера пересылки используйте любой
общедоступный DNS сервер
## 11. Настройте часовой пояс на всех устройствах, согласно месту проведения
экзамена.
Таблица 2. Таблица имен
Устройство Запись Тип
HQ-RTR hq-rtr.au-team.irpo A,PTR
BR-RTR br-rtr.au-team.irpo A
HQ-SRV hq-srv.au-team.irpo A,PTR
HQ-CLI hq-cli.au-team.irpo A,PTR
BR-SRV br-srv.au-team.irpo A
HQ-RTR moodle.au-team.irpo CNAME
HQ-RTR wiki.au-team.irpo CNAME
Необходимые приложения:
Приложение. Таблица с примером заполнения адресов устройств
Таблица 3. Пример заполнения адресов устройств
Имя устройства IP-адрес Шлюз по умолчанию
BR-SRV 192.168.0.2/24 192.168.0.1


