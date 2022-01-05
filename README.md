# traefik-as-a-reverse-proxy
Using Traefik as a reverse proxy to run multiple applications on one Docker Host.

## Generate ADMIN password

`sudo apt-get install apache2-utils`

Replace *secure_password* with your admin password

`htpasswd -nb admin secure_password`

The result of this command should be like this:

`admin:$apr1$iZ5.nYAO$7ma8gQjB3VMrYvAhn3WwH.`

Copy every character after **admin:** and paste it on dynamic.yml file insted of "PASSWORD" (between the quotes).
