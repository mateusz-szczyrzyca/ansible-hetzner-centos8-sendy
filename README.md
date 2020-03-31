PL:

Pliki do artykułu: https://devopsiarz.pl/kurs-ansible/yt-livestream-tworzenie-i-deploy-wlasnej-listy-mailingowe-sendy-aws-ses/

Zanim użyjesz, przeczytaj artykuł. 

To playbooki przetestowane na następującej konfiguracji:

- CentOS8 w Hetzner Cloud (domyślne logowanie po kluczu SSH)
- SELinux włączony
- sendy-4.0.6
- Caddy jako web server
- MariaDB jako baza danych
- php-fpm

Pamiętaj, aby ustawić swoje hasła i użytkowników w pliku `host_vars/nazwa_twojeg_hosta/passwords.yml` i użyć 
`ansible-vault crypt` celem zaszyfrowania go.

EN:

These are files related to polish article: https://devopsiarz.pl/kurs-ansible/yt-livestream-tworzenie-i-deploy-wlasnej-listy-mailingowe-sendy-aws-ses/

`newsletter.yml` is a playbook which deploys and installing sendy-4.0.6 along with caddy 
web server, MariaDB database and PHP. Sendy is a newsletter PHP application which you [can buy here](https://sendy.co)'

`backup_database.yml` is a playbook which create backup of the database and downloads it on your local control machine.

Remember about setting your preferred credentials in `hosts_vars/your_host_name/password.yml` and use 
`ansible-vault crypt` command afterwards to secure this file.
