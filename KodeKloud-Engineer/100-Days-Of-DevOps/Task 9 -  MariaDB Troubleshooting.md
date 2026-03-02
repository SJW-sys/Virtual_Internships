# MariaDB Troubleshooting
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> There is a critical issue going on with the Nautilus application in Stratos DC. The production support team identified that the application is unable to connect to the database. After digging into the issue, the team found that mariadb service is down on the database server.
>
> Look into the issue and fix the same.

## Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

0. (not possible in lab) typically I would consider snapshotting the server, or reviewing when the last snap shot was.

1. Connect to target server, login details found in the 'company' wiki. (In a real world this would be in a vault,or you be accessing via your own assigned identity, not a shared identity.)

    ssh peter@stdb01

2. review Mariadb status

    sudo systemctl status mariadb

3. attempt a simple restart, suspect it will not work, and if it does contiune till root cause can be fixed

    sudo systemctl start mariadb

3. review logs

    journalctl -xeu mariadb.service

        Mar 02 19:38:12 stdb01.stratos.xfusioncorp.com mariadb-prepare-db-dir[2286]: Database MariaDB is not initialized, but the directory /var/lib/mysql is not empty, so initialization cannot be done.
        Mar 02 19:38:12 stdb01.stratos.xfusioncorp.com mariadb-prepare-db-dir[2286]: Make sure the /var/lib/mysql is empty before running mariadb-prepare-db-dir.
        Mar 02 19:38:12 stdb01.stratos.xfusioncorp.com systemd[1]: mariadb.service: Child 2286 belongs to mariadb.service.
        Mar 02 19:38:12 stdb01.stratos.xfusioncorp.com systemd[1]: mariadb.service: Control process exited, code=exited, status=1/FAILURE

    looks like a potential error with expected dir missing, or wrong permissions, or unexpected data.

4. reviewed dir causing issue

    ls -al /var/lib/

        drwxr-xr-x 1 root  root  4096 Mar  2 19:32 . </br>
        drwxr-xr-x 1 root  root  4096 Mar  2 19:32 .. </br>
        drwxr-xr-x 1 root  root  4096 Aug 29  2025 alternatives </br>
        drwxr-xr-x 1 root  root  4096 Aug 29  2025 dnf </br>
        drwxr-xr-x 2 root  root  4096 Jun 25  2024 games </br>
        drwxr-xr-x 2 root  root  4096 Jun 25  2024 misc </br>
        drwxr-xr-x 4 mysql mysql 4096 Mar  2 19:32 mysqld </br>
        drwx------ 2 root  root  4096 Aug 29  2025 private </br>
        drwxr-xr-x 1 root  root  4096 Mar  2 19:21 rpm </br>
        drwxr-xr-x 2 root  root  4096 Jun 25  2024 rpm-state </br>
        drwxr-xr-x 3 root  root  4096 Aug 26  2025 selinux </br>
        drwxr-xr-x 1 root  root  4096 Mar  2 19:32 systemd </br>
        drwxr-xr-x 1 root  root  4096 Aug 29  2025 tpm2-tss </br>

    no directory, what does exist is misnamed, but does have correct permissions. Reviewed online resources to ensure mysqld is not expected file for something else with mysql.

5. looks like somehow the dir got renamed wrong, I will backup and compress existing data before executing to prevent data loss. Again should have a snapshot of the vm if possible.

    sudo tar -czf /home/peter/mysql_error_02-02-26.tar.gz /var/lib/mysqld

6. rename the suspected file

    sudo mv /var/lib/mysqld /var/lib/mysql

7. validate change, ensuring permissions are still correct.

    ls -al /var/lib/

8. attempt to bring mariadb up

    sudo systemctl start mariadb

9. validate service working and ensure enabled

    sudo systemctl status mariadb

10. validate the data itself

    sudo mysql </br>
    SHOW DATABASES; </br>
    EXIT;

11. submit

12. (outside the lab) Once its been running for some period of time and validated as working as intended, I would remove the tar and the snapshot of the server I took. I would also update ticket, and follow up with team to be on the lookout for rename issues in the future.

## My Comments
Considering this is a database, and the only one, its critical you take a approach to ensure no data loss.


