# traefik-as-a-reverse-proxy
Using Traefik as a reverse proxy to run multiple applications on one Docker Host.

## Generate ADMIN password

`sudo apt-get install apache2-utils`

Replace *secure_password* with your admin password

`htpasswd -nb admin secure_password`

The result of this command should be like this:

`admin:$apr1$iZ5.nYAO$7ma8gQjB3VMrYvAhn3WwH.`

Copy every character after **admin:** and paste it on dynamic.yml file insted of "PASSWORD" (between the quotes).

## Create the 'proxy' Docker network
For assuring to apps can see each other create the proxy network specified on the **docker-compose.yml** file

`docker network create proxy`

## Give 600 permission to acme.json
For allowing the generation of the SSL certifictes with let's encrypt we must set the permission 600 to **/traefik-configurations/traefik-data/acme.json**

chmod 600 acme.json

If you have problem at this point seemed like this:

![image](https://user-images.githubusercontent.com/15148230/197367768-7f302511-c21b-4e02-b1ac-8dcfd2bc5aa1.png)

Try to delete the acme.json file, create it again and give 600 permission:

`rm -rf acme.json`

`touch acme.json`

`chmod 600 acme.json`

## Run Docker compose

Go to the folder /traefik-configurations and execute:

`docker compose up -d`
