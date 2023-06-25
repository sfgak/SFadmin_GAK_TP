Repo for ansible-playbooks for Total Project

In a "playbooks" folder of this repo placed ansible playbooks for:
1. Correct DNS client settings for YandexCloud virtual machines
- YC-dns-client.yml

2. Setting up the timesync service (adjusting the time zone and enabling time synchronization over the ntp protocol)
- ntp-configure.yml

3. Install and configure LEMP stack (LAMP stack with nginx web-server configured as a reverse proxy)
- lemp-install-without-ssl.yml

4. Acquiring and getting Let's Encrypt SSL certificate
- get-LE-SSL-cert.yml
!!! Note !!!
The description files of the hosts (servers to which this playbook will be applied) must be contained
This playbook is written in such a way that, unfortunately, it can only be applied to one server at a time.
In order to apply it to another server, you need to: 
1) Check for the file /etc/ansible/host_vars/<server_name> with the following contents:
---
acme_challenge_type: http-01
acme_directory: https://acme-v02.api.letsencrypt.org/directory
acme_version: 2
acme_email: any@domain.com
letsencrypt_dir: /etc/lets'encrypt
letsencrypt_keys_dir: /etc/letsencrypt/keys
letsencrypt_csrs_dir: /etc/letsencrypt/cars
letsencrypt_certs_dir: /etc/letsencrypt/certs
letsencrypt_account_key: /etc/letsencrypt/account/account.key
domain_name: <Server's public domain name>
2). Correct the variable name acmechallengeXXXXXXXXXXXXnipio so that instead of XXXXXXXXXXXX the public IP address of the server to which this playbook will be applied is specified.
!!! End of Note !!!

5. Applying Let's Encrypt SSL certificate for nginx in LEMP stack
- lemp-apply-LE-SSL-cert.yml

6. Install and configure the OpenVPN client on a production server. For security purposes, the configuration for the OpenVPN client is generated on the OpenVPN server
- install-openvpn-client-prod.yml

7. Install and configure the OpenVPN client on the test server. For security purposes, the configuration for the OpenVPN client is generated on the OpenVPN server
- install-openvpn-client-test.yml

8. Install and configure Zabbix-agent 6.0.18 on production servers. The configuration is sewn into the playbook
- install-zabbix-agent.yml

9. Install filebeat. For security reasons and because of the different sets of roles on the servers, filebeat is configured manually.
- install-filebeat.yml 

Installation and configuration of Ansible, OpenVPN Server, Zabbix server, Filebeat, Grafana, Postfix, Dovecot, bind9, ETC, PostgreSQL, pgadmin was done manually.
PS. Filebeat is installed via playbook, and its configuration is done manually.
