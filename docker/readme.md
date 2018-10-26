##Установка docker на debian
https://docs.docker.com/install/linux/docker-ce/debian/

`apt-get remove docker docker-engine docker.io`

`apt-get install apt-transport-https ca-certificates curl gnupg2 software-properties-common`

`curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -`
(может долго выполняться)

`apt-key fingerprint 0EBFCD88`

`add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"`

`apt-get update`
(Если в результате выдал ошибку, то нужно раскоментировать последнюю строку, выполнить ещё раз `apt-get update` затем закоментировать и опять `apt-get update`)

`apt-get install docker-ce docker-compose`

Добавить пользователя в группу docker:
`usermod -aG docker $USER`

##Создание образа

`docker build -t zaek_php -f zaek-php-image.docker .`

`docker build -t zaek_mysql zaek-mysql-image.docker`

##Запуск контейнера

`cd docker` - перейти в директорию docker
 
`docker-compose up` - запустить docker
 
`docker exec -i -t $( docker ps | grep 'zaek_nginx' | awk '{print $1}') bash` - открыть консоль на сервере nginx   


##Настройка

**Порт веб-сервера** docker-compose.yml: services -> nginx -> ports "`PORT`:80" 