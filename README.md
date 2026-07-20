# PXE

## Schema

ansible/
├── inventories/
│   ├── dev/
│   └── prod/
│
├── playbooks/
│   ├── pxe.yml
│   ├── dns.yml
│   └── web.yml
│
├── roles/
│   ├── dhcp/
│   ├── tftp/
│   ├── nginx/
│   ├── apache/
│   ├── dns/
│   ├── ipxe/
│   └── firewall/
│
└── group_vars/

roles/
├── dhcp        # DHCP-сервер
├── dns         # DNS (если нужен)
├── tftp        # TFTP и загрузчики (pxelinux.0, ipxe.efi и т.п.)
├── nginx       # или apache — только настройка веб-сервера
├── ipxe        # меню iPXE, kernel, initrd, Kickstart/Preseed, ISO
├── firewall    # правила firewall
└── selinux     # при необходимости настройка SELinux


role: dhcp
Устанавливает dhcpd; генерирует dhcpd.conf; запускает сервис.
roles/dhcp/
tasks/
templates/
defaults/

role: tftp
Устанавливает tftp-server; создает каталог /var/lib/tftpboot; кладет ipxe.efi; кладет undionly.kpxe; запускает сервис.
roles/tftp/
tasks/
templates/
files/

role: nginx
Устанавливает nginx; настраивает виртуальный хост; открывает firewall; запускает сервис.

role: ipxe
Копирует меню; копирует kernel; копирует initrd; копирует kickstart; копирует ISO.

role: firewall
Она откроет: 69/udp; 80/tcp; 443/tcp; 67/udp; 4011/udp.

playbook
- hosts: pxe
  roles:
    - firewall
    - dhcp
    - tftp
    - nginx
    - ipxe

Если DNS тоже на этом сервере:
roles:
  - firewall
  - dns
  - dhcp
  - tftp
  - nginx
  - ipxe

DHCP и DNS находятся на другом сервере:
- hosts: dns
  roles:
    - dns
    - dhcp
- hosts: pxe
  roles:
    - firewall
    - tftp
    - nginx
    - ipxe
