MariaDB 10.3 with MariaDB backup
=========

This playbook will install MariaDB 10.1 and the MariaDB backup script on the host.
The mariadb work directory will be located at `/home/mysql`.

Requirements
------------

This script is for CentOS 7 only.

Please install the `provision.yml` playbook first.

Provide the `secondary_user` in the `db.yml`'s  `remote_user` for login.

Please place the `server-ip` at the `hosts` block in the `db.yml` file.

The default is connecting to local machine.

Role Variables
--------------

Uncomment `USE_BACKUP` in the `/roles/db/vars/main.yml` var file for using mariabackup and keep 20 days backup data function in the crontab job.

The variables example is as below. It will create a backup user in database for executing the `mariabackup.sh` script.

    # USE_BACKUP: 20
    BACKUP_USER: backup
    BACKUP_USER_PASS: backup123


Usage
----------------

After the provision, you can run the playbook directly as bleow :

`ansible-playbook db.yml`

or only need install the MariaDB backup script cron job.

`ansible-playbook db.yml --tags "backup_only"`


License
-------

BSD

Author Information
------------------

Ricky Chen
