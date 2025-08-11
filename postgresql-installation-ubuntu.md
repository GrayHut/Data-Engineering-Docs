# Uninstallation & re-installation guide for PostgreSQL DB for Ubuntu

## Uninstalling PostgreSQL

- Check the currently installed postgresql database by checking the version using: **`psql –version`**
- If postgresql is installed, disable it using: **`sudo systemctl disable postgresql`**
- Proceed to stop the postgresql using: **`sudo systemctl stop postgresql`**
- Uninstall postgresql using: **`sudo apt remove –purge postgresql postgresql-contrib postgresql-*`**

## Installing Postgresql

- Postgresql installation command: **`sudo apt install postgresql postgresql-contrib`**
- Enable and start postgresql using: **`sudo systemctl enable postgresql && sudo systemctl start postgresql`**
- Verify installation by checking the postgresql version: **`psql –version`**

## Additional settings (After installation)

- Set a password for the default user (postgres): **`sudo -u postgres psql -c “ALTER USER postgres WITH PASSWORD ‘your-password’;”`**
- Create a database with the user postgres: **`sudo -u postgres psql -c “CREATE DATABASE {name-of-database};”`**
- Grant user postgres all privileges to the created database: **`sudo -u postgres psql -c “GRANT ALL PRIVILEGES ON DATABASE {name-of-database} TO postgres;”`**

*From here you can proceed and add tables to the database you've created if you wish...*

## Installation of psycopg2
psycopg2 is the python adapter for Postgresql.

- Install psycopg2 dependencies (preferably within a virtual environment): **`sudo apt install python3-dev libpg-dev`**
- Psycopg2 installation: **`sudo apt install psycopg2-binary`**

## Database Connection String
Once the local postgresql database is installed, you are now able to use the following format of the Database Connection String for various applications (such as connection to Apache Airflow): 

**`postgresql+psycopg2://postgres:PASSWORD@localhost:5432/DATABASE`**