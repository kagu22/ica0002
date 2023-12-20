### Install and configure infrastructure with Ansible:


```ruby
ansible-playbook infra.yaml
```

### Restore MySQL data from the backup: 


```ruby
sudo -u backup duplicity --no-encryption restore rsync://kagu22@backup.kaguu.rk//home/kagu22/mysql/ /home/backup/restore/
```

```ruby
mysql agama < /home/backup/restore/agama.sql
```


### Restore InfluxDB data from the backup


```ruby
sudo -u backup duplicity --no-encryption restore rsync://kagu22@backup.kaguu.rk//home/kagu22/influxdb/ /home/backup/restore
```

```ruby
service telegraf stop
```

```ruby
influx -execute 'DROP DATABASE telegraf'
```

```ruby
influxd restore -portable -database telegraf /home/backup/restore
```


After that run ansible-playbook again.

