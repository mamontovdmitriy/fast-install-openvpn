# Быстрая настройка OpenVPN Server через Ansible

## Предварительная подготовка рабочего места

### Установить Ansible 
Инструкция по установке: https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-on-ubuntu

### Клонировать репозиторий  

    git clone https://github.com/mamontovdmitriy/fast-install-openvpn.git
### Скачать зависимости 
Загрузить используемые роли в подкаталог `roles`:
- EasyRSA https://github.com/nkakouros-original/ansible-role-easyrsa    
- Stouts.openvpn https://github.com/Stouts/Stouts.openvpn

## Установка и настройка OpenVPN Server

### Настроить на сервере вход по сертификату (не обязательно)
Ссылка на инструкцию.

### Задать IP-адрес сервера
Замените в файле `hosts.yml` значение `{YOUR_SERVER_IP}` на  IP-адрес вашего сервера.

### Запустить скрипт установки 
В терминале выполнить команду

    ansible-playbook -i hosts.yml vpn.yml


# Ответы на вопросы
### Где лежат сертификаты для подключения клиентов?
Файлы для подключения находятся на сервере в каталоге `/etc/openvpn/ovpns/*`.
Забрать их на компьютер можно командой

    scp root@{YOUR_SERVER_IP}:/etc/openvpn/ovpns/* ./
### Какой пароль по-умолчанию для подключения к VPN-серверу?
В конфигурации по-умолчанию создается два клиента `client1` и `client2` с паролем `password123456`.
### Где взять подходящий сервер?
Доступный хостинг под VPN и не только: https://my.vdsplanet.net/?affid=32
