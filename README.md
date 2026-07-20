# DevOps Toolkit

Набор Ansible-ролей для развёртывания компонентов PXE-инфраструктуры.

Проект находится в разработке и пока не предназначен для production.

## Роли

- `dhcp` — установка и настройка `isc-dhcp-server`;
- `tftp` — установка TFTP-сервера;
- `nginx` — установка веб-сервера;
- `dns` — установка DNS-сервера.

Подробности и переменные находятся в README каждой роли.

## Структура

```text
playbooks/   # Playbook-файлы
roles/       # Ansible-роли
ansible.cfg  # Настройки Ansible
```

## Пример запуска

Подготовьте inventory с группой `dhcp_servers`, затем выполните:

```bash
ansible-playbook -i inventory.ini playbooks/dhcp.yaml
```

Для выполнения задач на целевых серверах необходимы права `become`.
