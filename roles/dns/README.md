# Роль DNS

Роль для установки и настройки BIND9 на Debian/Ubuntu.

Проект находится в разработке. Сейчас подготовлены задачи для:

- установки пакетов BIND9;
- резервного копирования конфигурации;
- настройки ACL для доверенных подсетей;
- настройки блока `options`;
- объявления прямой и обратной DNS-зон;
- проверки конфигурации через `named-checkconf`;
- перезапуска BIND9 при изменениях.

## Основные переменные

```yaml
dns_trusted_networks:
  - 192.168.0.0/16

domain: dark.side.com
```

Для настройки зон ожидаются узлы `dns01` и `dns02` с адресами `ansible_host` в inventory.

Создание файлов прямой и обратной зон будет добавлено позже.

Основа конфигурации: [DigitalOcean — BIND on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-a-private-network-dns-server-on-ubuntu-22-04).
