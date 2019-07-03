## Install docker on debian
https://docs.docker.com/install/linux/docker-ce/debian/

`apt-get remove docker docker-engine docker.io`

`apt-get install apt-transport-https ca-certificates curl gnupg2 software-properties-common`

`curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -`

`apt-key fingerprint 0EBFCD88`

`add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"`

`apt-get update`
(if you see an error uncomment the penult line (add-apt-repository ... ) and run again `apt-get update`)

`apt-get install docker-ce docker-compose`

Add user group docker:
`usermod -aG docker $USER`

## Making an image

`docker build -t zaek_php -f zaek-php-image.docker .`

`docker build -t zaek_mysql zaek-mysql-image.docker`

## Start container

`cd docker`
 
`docker-compose up` - start docker
 
`docker exec -i -t $( docker ps | grep 'PROJECT_NAME_nginx' | awk '{print $1}') bash` open console on server nginx (use you own PROJECT_NAME)


## Settings

All settings are present in .env.example file
