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

These playbooks have been tested in the following configuration:

- Hetzner Cloud instance with CentOS8 (SSH key as a default login method)
- SELinux enabled
- sendy-4.0.6 as a sendy version
- Caddy as a web server
- MariaDB as a database
- php-fpm

`newsletter.yml` is a playbook which deploys and installing sendy-4.0.6 along with caddy 
web server, MariaDB database and PHP. Sendy is a newsletter PHP application which you [can buy here](https://sendy.co). 
It uses [Amazon SES](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/Welcome.html) to send your mails, hence your need 
your Amazon AWS account.

`backup_database.yml` ~~is a playbook which create backup of the database and downloads it on your local control machine.~~ DEPRECATED: it has been transformed to a role

Remember about setting your preferred credentials in `hosts_vars/your_host_name/password.yml` and use 
`ansible-vault crypt` command afterwards to secure this file.

`update-sendy.yml` updates sendy installation on-the-fly and makes backup of the database. Download sendy archive (usually in format `sendy-<version>.zip`) and use by the following command (example for sendy-5.0):

`$ ansible-playbook -u www update-sendy.yml -e "sendy_archive=sendy-5.0.zip"`