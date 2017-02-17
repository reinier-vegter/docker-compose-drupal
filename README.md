
# Get started

## Common apps (mysql, DNS etc)
Start common  apps like mysql and mailhog (you need those first):
`export MYSQL_DATA=/my/mysql/datafolder; cd /path/to/docker-compose-drupal/common-apps && docker-compose up -d`
Add this command to your boot-scripts.


This gives you
 - mysql:    1 mysql-container for all persistent databases.
             Available at localhost:3306 and from your containers at mysql.dev .
 - mailhog:  This is a mailsink with web UI where php-containers will send all email to.
             Note that only containers started with the project docker-compose.yml from this repo will use this!
             Available at http://mailhog.dev:8025/
 - devdns:   This is the central dns-container that provides you the .dev domain and project hostnames.
             If this is not started, functionality from this repo won't work well (if not at all).


## To get DNS to work on your host / laptop, follow instructions:

### Ubuntu:
   edit /etc/dhcp/dhclient.conf
   add:
      supersede domain-name "dev";
      prepend domain-name-servers 127.0.0.1;
   see: https://github.com/ruudud/devdns


## Run a project
Copy `drupal-project/docker-compose.yml` and `drupal-project/.env` to you project.
Edit `.env`.
Run `docker-compose up -d`.
To stop, run `docker-compose down`.

## Slow filesystem om OSX
Try to use `d4d-unison-sync` in drupal-project/docker-compose.yml .
Have not tested with it yet, so you're on your own.
Read http://docs.docker4drupal.org/en/latest/macos/ .

# Extra info

## PHP logs

Run `docker-compose logs -f php` from your project folder to tail the php logs.

