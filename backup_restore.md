Install and configure infrastructure with Ansible:

    ansible-playbook infra.yaml

Restore MySQL data from the backup:

sudo -u backup duplicity --no-encryption restore rsync://kagu22@backup.kaguu.rk//home/kagu22/mysql/ /home/backup/restore/
mysql agama < /home/backup/restore/agama.sql


Restore InfluxDB data from the backup

sudo -u backup duplicity --no-encryption restore rsync://kagu22@backup.kaguu-rk//home/kagu22/influxdb/ /home/backup/restore
service telegraf stop
influx -execute 'DROP DATABASE telegraf'
influxd restore -portable -database telegraf /home/backup/restore

After that run ansible-playbook again.

