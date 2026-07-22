# Роль DHCP

Source: Hands-On Enterprise Automation on Linux, James Freeman.

Устанавливает и настраивает `isc-dhcp-server` на Debian/Ubuntu.

Роль выполняет следующие действия:

- устанавливает пакет DHCP-сервера;
- сохраняет резервную копию `/etc/dhcp`;
- копирует `dhcpd.conf`;
- запускает сервис и добавляет его в автозагрузку;
- перезапускает сервис при изменении конфигурации.

## Основные переменные

```yaml
dhcp_user: root
dhcp_group: root
dhcp_backup_path: /opt/backups
```

## Пример подключения

```yaml
- name: Configure DHCP server
  hosts: dhcp_servers
  become: true
  gather_facts: true

  roles:
    - dhcp
```

Конфигурация сервера находится в `files/dhcpd.conf`.
