# Linux System Administration & Server Management

  ---------------------------------------------------------------------------------------------
                     ID Main Category    Sub Category         Topic
  --------------------- ---------------- -------------------- ---------------------------------
                      1 Linux            Linux Installation   Ubuntu/RHEL/Debian Installation,
                        Fundamentals                          Partitioning, Bootloader

                      2 Linux            Linux File System    / (root), /home, /etc, /var,
                        Fundamentals                          /usr, /tmp, /proc

                      3 Linux            Basic Linux Concepts CLI basics, man pages, pipes,
                        Fundamentals                          redirection, grep, awk, sed

                      4 Linux            User Management      useradd, usermod, userdel,
                        Fundamentals                          passwd, /etc/passwd, /etc/shadow

                      5 Linux            File Permissions     chmod (755/644), chown, chgrp,
                        Fundamentals                          umask, SUID, SGID, Sticky Bit

                      6 Linux            Package Management   apt (Debian/Ubuntu), yum/dnf
                        Fundamentals                          (RHEL/CentOS), dpkg, rpm

                      7 Networking for   IP Address           ifconfig, ip addr,
                        Linux Servers    Configuration        /etc/network/interfaces, Netplan

                      8 Networking for   Gateway              route add default, ip route,
                        Linux Servers    Configuration        /etc/network/interfaces

                      9 Networking for   DNS Configuration    /etc/resolv.conf, nameserver,
                        Linux Servers                         /etc/hosts

                     10 Networking for   Hostname Setup       hostnamectl, /etc/hostname,
                        Linux Servers                         /etc/hosts update

                     11 Networking for   Static IP Setup      Netplan (Ubuntu),
                        Linux Servers                         /etc/sysconfig/network-scripts/
                                                              (RHEL)

                     12 Networking for   SSH Access           ssh client, ssh-keygen,
                        Linux Servers                         ssh-copy-id,
                                                              \~/.ssh/authorized_keys

                     13 Service          systemd              systemctl commands, unit files,
                        Management                            targets (runlevels)

                     14 Service          Service              systemctl
                        Management       Start/Stop/Restart   start/stop/restart/reload

                     15 Service          Enable Auto Start    systemctl enable/disable,
                        Management       Services             systemctl is-enabled

                     16 Web Server       Nginx Installation   apt install nginx, yum install
                        Administration                        nginx, verify with systemctl

                     17 Web Server       Nginx Virtual Host   server block, server_name, root,
                        Administration                        index, sites-available/enabled

                     18 Web Server       Nginx Reverse Proxy  proxy_pass, proxy_set_header,
                        Administration                        upstream

                     19 Web Server       Nginx SSL            Let's Encrypt, certbot, SSL
                        Administration   Configuration        certificates, HTTPS redirect

                     20 Web Server       Apache Installation  apt install apache2, yum install
                        Administration                        httpd

                     21 Web Server       Apache Virtual Host  VirtualHost, ServerName,
                        Administration                        DocumentRoot, Directory directive

                     22 Web Server       Apache PHP           libapache2-mod-php, php-fpm, .php
                        Administration   Integration          files handling

                     23 Database Server  MySQL/MariaDB        apt install mariadb-server,
                        Administration   Installation         mysql_secure_installation

                     24 Database Server  Create Database      CREATE DATABASE, SHOW DATABASES,
                        Administration                        USE database

                     25 Database Server  User & Permission    CREATE USER, GRANT, REVOKE, FLUSH
                        Administration   Management           PRIVILEGES

                     26 Database Server  Backup & Restore     mysqldump, mysql \< backup.sql,
                        Administration                        cron automated backup

                     27 DNS Server       Bind9 Installation   apt install bind9, named service,
                        Administration                        /etc/bind/

                     28 DNS Server       Zone File            /etc/bind/named.conf.local, zone
                        Administration   Configuration        definition

                     29 DNS Server       Forward Lookup Zone  A records, CNAME, TXT, TTL, SOA,
                        Administration                        NS

                     30 DNS Server       Reverse Lookup Zone  PTR records, in-addr.arpa,
                        Administration                        ip6.arpa

                     31 DHCP Server      IP Pool              isc-dhcp-server, subnet
                        Administration   Configuration        declaration, range

                     32 DHCP Server      Lease Management     /var/lib/dhcp/dhcpd.leases, lease
                        Administration                        time, default/max lease

                     33 DHCP Server      Reservation Setup    host declaration, hardware
                        Administration                        ethernet, fixed-address

                     34 File Server      Samba Installation   apt install samba, smb.conf,
                        Administration                        smbpasswd

                     35 File Server      Samba Windows        \[share\] definition, workgroup,
                        Administration   Sharing              browseable, read/write

                     36 File Server      NFS Installation     apt install nfs-kernel-server,
                        Administration                        /etc/exports

                     37 File Server      NFS Linux Sharing    exportfs, showmount, mount -t
                        Administration                        nfs, /etc/fstab

                     38 FTP/SFTP Server  vsftpd Setup         apt install vsftpd,
                        Administration                        /etc/vsftpd.conf, anonymous/local
                                                              user

                     39 FTP/SFTP Server  SFTP using SSH       internal-sftp, ChrootDirectory,
                        Administration                        Subsystem sftp

                     40 FTP/SFTP Server  User Restriction &   chroot_local_user,
                        Administration   Security             allow_writeable_chroot, userlist

                     41 Mail Server      Postfix              MTA, main.cf, myhostname,
                        Basics                                mydestination, relayhost

                     42 Mail Server      Dovecot              MDA, IMAP/POP3, dovecot.conf,
                        Basics                                10-master.conf, 10-mail.conf

                     43 Mail Server      SMTP Basics          Port 25, 587, 465, relay, auth
                        Basics                                

                     44 Mail Server      IMAP Basics          Port 143, 993, folder sync,
                        Basics                                mailbox access

                     45 Firewall &       UFW (Ubuntu)         ufw enable, allow/deny, status
                        Security                              

                     46 Firewall &       Firewalld            firewall-cmd, zones
                        Security         (RHEL/CentOS)        

                     47 Firewall &       Open Ports           ufw allow 22/tcp, add-port
                        Security                              

                     48 Firewall &       Block Ports          ufw deny 23/tcp, remove-port
                        Security                              

                     49 Firewall &       SSH Allow Rules      allow subnet to port 22
                        Security                              

                     50 Firewall &       NAT Basics           iptables nat, MASQUERADE
                        Security                              

                     51 Monitoring &     journalctl           service logs, follow, boot
                        Logs                                  

                     52 Monitoring &     syslog               /var/log/syslog, rsyslog
                        Logs                                  

                     53 Monitoring &     top                  CPU/Memory monitoring
                        Logs                                  

                     54 Monitoring &     htop                 Enhanced top
                        Logs                                  

                     55 Storage          Disk Partitioning    fdisk, gdisk, parted
                        Management                            

                     56 Storage          Mounting             mount, umount, /etc/fstab
                        Management                            

                     57 Storage          LVM                  pvcreate, vgcreate, lvcreate
                        Management                            

                     58 Storage          Disk Usage Analysis  df, du, ncdu
                        Management                            

                     59 Backup System    rsync                Local/remote sync

                     60 Backup System    tar                  archive/compress

                     61 Backup System    gzip                 Compression

                     62 Backup System    Automated Backup     cron + rsync

                     63 SSH & Remote     SSH Hardening        Port, MaxAuthTries, AllowUsers
                        Administration                        

                     64 SSH & Remote     Key-Based            ssh-keygen, config
                        Administration   Authentication       

                     65 SSH & Remote     Disable Root Login   PermitRootLogin no
                        Administration                        

                     66 Shell Scripting  Bash Scripting       variables, loops, if, functions
                        & Automation                          

                     67 Shell Scripting  Cron Jobs            crontab syntax
                        & Automation                          

                     68 Shell Scripting  Automation Tasks     backup, monitoring
                        & Automation                          

                     69 Virtualization   KVM                  libvirt, qemu

                     70 Virtualization   VMware               ESXi, vSphere

                     71 Virtualization   VirtualBox           NAT, Bridged, snapshots

                     72 Container Basics Docker               run, images, exec

                     73 Container Basics Docker Images        Dockerfile basics

                     74 Container Basics Docker Compose       services, volumes

                     75 Linux Security   fail2ban             Jails
                        Hardening                             

                     76 Linux Security   SELinux Basics       getenforce, semanage
                        Hardening                             

                     77 Linux Security   AppArmor             profiles
                        Hardening                             

                     78 Linux Security   SSH Security         key-only
                        Hardening                             

                     79 Linux Security   Permission Hardening umask, SUID
                        Hardening                             

                     80 Monitoring Tools Zabbix               Server/Agent

                     81 Monitoring Tools Nagios               NRPE, plugins

                     82 Cloud Linux      AWS EC2              Instance launch
                        Basics                                

                     83 Cloud Linux      Security Groups      Inbound/outbound
                        Basics                                

                     84 Cloud Linux      Linux Deployment in  Cloud-Init, AMI
                        Basics           Cloud                

                     85 Automation &     Git                  clone, commit, push
                        DevOps Starter                        

                     86 Automation &     CI/CD Basics         Jenkins, GitHub Actions
                        DevOps Starter                        

                     87 Automation &     API Basics           REST, curl, JSON
                        DevOps Starter                        
  ---------------------------------------------------------------------------------------------
