# Web application deployment with docker and nginx

Web application deployment using docker, docker-compose and manage multiple environment like production, stating etc.

## Docker compose file modification ex- docker image, volume mapping, configuration file
- Open docker-compose.yml file and update the service and images you will be using for each service as per instruction in the compose file.

## Database configuration ex- username, db, password
- Modify .env file and set corresponding values related to database and application specific secrect values.  

Run database service service defined in docker-compose.yml file
```
$ docker-compose up -d db
$ docker-compose exec db bash
$ mysql -uroot -p
```
Note:
- Create application specific database
- Create application specific user and grant previlidges to the database

Run appication service defined in the docker-compose.yml file
```
$ docker-compose up -d app
$ docker-compose exec app bash
$ bundle exec rake db:migrate
$ bundle exec rake db:seed
$ exit
```

## Nginx configuration file modification
- Modify nginx.conf file which is located under ```nginx/nginx.conf``` file. You can find the instructions in the config file where you might need to change as per your application setup. 
- For ssl configuration enable ```nginx/nginx.ssl.conf``` file in the docker-compose file under web service and do the necessary changes like above. 

Finally run nginx web server defined in docker-compose.yml file
``` 
$ docker-compose up -d web
```


