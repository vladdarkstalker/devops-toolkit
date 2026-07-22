# Роль DNS

Роль для установки и настройки BIND9 на Debian/Ubuntu.

Проект находится в разработке. Сейчас подготовлены задачи для:

- установки пакетов BIND9;
- резервного копирования конфигурации;
- настройки ACL и блока `options`;
- проверки конфигурации через `named-checkconf`;
- перезапуска BIND9 при изменениях.

## Inventory

Для формирования ACL ожидаются узлы `dns01` и `dns02` с адресами `ansible_host`:

```ini
[dns_servers]
dns01 ansible_host=10.128.10.11
dns02 ansible_host=10.128.20.12
```

Настройка `named.conf.local` и файлов зон будет добавлена позже.

Основа конфигурации: [DigitalOcean — BIND on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-a-private-network-dns-server-on-ubuntu-22-04).
