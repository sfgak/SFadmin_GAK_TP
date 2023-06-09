Repo for ansible-playbooks and *.conf-files, placed in /etc for Total Project

In a "playbooks" folder of this repo placed ansible playbooks for:
1. Correct DNS client settings for YandexColud virtual machines
- YC-dns-client.yml
2. Install and configure LEMP stack (LAMP stack with nginx web-server configured as a reverse proxy)
- lemp-install-without-ssl.yml
3. Acquiring and getting Let's Encrypt SSL certificate
- get-LE-SSL-cert.yml
4. Applying Let's Encrypt SSL certificate for nginx in LEMP stack
- lemp-apply-LE-SSL-cert.yml

In 52, 64, 65, 85 lines of playbook, that acquires and gets Let's Encrypt SSL certificate, in a 'acmechallengeXXXXXXXXXXXXnipio' variable place public IP-address of LEMP server without dots '.'
