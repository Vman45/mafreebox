- vous trouverez ici les éléments nécessaire pour interconnecter telegraf à la freebox via son API.
- ce système fonctionne sur une raspbian stretch avec un raspberry PI.

ci-joint la procédure d'installation :

```/bin/bash
# copier l'ensembe de ces fichiers sur le rasp
scp * pi@rasp

# se loger sur le rasp
ssh pi@rasp
sudo bash

# vérifier que telegraf est installé ; le cas échéant procéder à son installation
dpkg -l | grep telegraf
ii  telegraf          1.9.0-1            armhf     Plugin-driven server agent for reporting metrics into InfluxDB.

# copier le fichier input-exec-mafreebox.conf sur le répertoire de conf télégraf
cp input-exec-mafreebox.conf /etc/telegraf/telegraf.d

# créer le répertoire mafreebox contenant l'ensemble des éléments permettant l'acces à l'api et l'insertion dans
# la base influx, via telegraf
mkdir -p /etc/telegraf/telegraf.d/mafreebox
cp freebox-influx.bash  influxdb.rb  input-exec-mafreebox.conf  mafreebox.yml /etc/telegraf/telegraf.d/mafreebox
chmod +x /etc/telegraf/telegraf.d/mafreebox/freebox-influx.bash
```

adapter sur le fichier mafreebox.yml en concordance avec les infos de connexion de votre API Freebox.

