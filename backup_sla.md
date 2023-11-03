BACKUP SERVICE SLA

BACKUP COVERAGE:
MySQL
InfluxDB
Ansible Repository

RPO (Recovery Point Objective)
Since we creating backups once a day every day, RPO is around 24 hours:
- Database Servers: 24 hours
- InfluxDB: 24 hours
- Ansible Repository: 24 hours

VERSIONING AND RETENTION
Every sunday full backup, every day only incremental backup.
Backups are stored for 28 days (4 weeks)

USABILITY CHECKS
Twice a week, on Tuesdays and Saturdays.

RESTORATION CRITERIA
Backup should be restored only if stored data was corrupted, stolen or deleted.

RTO (Recovery Time Objective)
8 hrs after the incident has been detected.

