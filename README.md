# mysql-azure-backup
Image prepared to backup MySQL database to Microsoft Azure.

This image is heavily based on [iainmckay/docker-mysql-backup](https://github.com/iainmckay/docker-mysql-backup).

There is a custom build available on the public registry at [neowaylabs/mysql-azure-backup](https://registry.hub.docker.com/u/neowaylabs/mysql-azure-backup/).

## Backing up

To backup run:

    $ docker run -e AZURE_STORAGE_ACCOUNT=account -e AZURE_STORAGE_ACCESS_KEY=key -e AZURE_STORAGE_CONTAINER=container -e MYSQL_HOST=127.0.0.1 -e MYSQL_USER=root -e MYSQL_PASSWORD=password neowaylabs/mysql-azure-backup backup

You can provide an extra argument with a specific database to backup.

## Restoring

To restore an existing backup run:

    $ docker run -e AZURE_STORAGE_ACCOUNT=account -e AZURE_STORAGE_ACCESS_KEY=key -e AZURE_STORAGE_CONTAINER=container -e MYSQL_HOST=127.0.0.1 -e MYSQL_USER=root -e MYSQL_PASSWORD=password neowaylabs/mysql-azure-backup restore

It is important to note that if this database already exists on your server, this process will drop it first. You can also provide an extra argument with a specific database to restore.

## Configuration

The container can be customized with these environment variables:

Name | Default Value | Description
--- | --- | ---
AZURE_STORAGE_ACCOUNT | `blank` | Your Azure storage account name to keep the backup
AZURE_STORAGE_ACCESS_KEY | `blank` | Your Azure storage access key to access the storage account
AZURE_STORAGE_CONTAINER | `blank` | The Azure storage container to keep the backup
MYSQL_HOST | 127.0.0.1 | Address the MySQL server is accessible at
MYSQL_PORT | 3306 | Port the MySQL server is accessible on
MYSQL_USER | root | User to connect as
MYSQL_PASSWORD | `blank` | Password to use when connecting
RESTORE_DB_CHARSET | utf8 | Which charset to recreate the database with
RESTORE_DB_COLLATION | utf8_bin | Which collation to recreate the database with
