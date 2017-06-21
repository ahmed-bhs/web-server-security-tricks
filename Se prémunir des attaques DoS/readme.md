Se prémunir des attaques DoS

Voilà l’attaque la plus connue. Le DoS (Denial of Service) a pour but de rendre indisponible votre serveur en faisant sauter vos services un par un. Le principe est simple : votre attaquant va envoyer un nombre important de demandes de synchronisation TCP jusqu’à envoyer votre serveur dans les choux.

Heureusement pour nous, il existe des outils pour contrer ce genre d’attaque. Le plus connu et certainement le plus fiable est fail2ban. Celui-ci va surveiller de prèt vos fichiers de log et va agir dès qu’il va rencontrer des erreurs redondantes en bannissant l’IP d’origine. De plus, il est très simple à mettre en place :
```php
sudo apt-get install fail2ban
```
Une fois installé, il suffit d’éditer le fichier de configuration /etc/fail2ban/jail.conf et d’activer les services qu’on souhaite protéger. Il est donc possible d’agir sur d’autres services tels que PHP, Apache, Postfix, etc.

Exemple :
```yaml
[ssh]
enabled  = true
port     = 1234
filter   = sshd
logpath  = /var/log/auth.log
maxretry = 6
```