# Dockering Reactome
To fully Dockerize Reactome, I am thinking of following this strategy:

1. Create a customized Dockerfile, consisting of the Reactome components. This can be further devided in to different docker containers, if the file gets to large or error-prone.

2. Using the above image(s) in a docker-compose file, using official MySQL and other images customized as per Reactome needs.

Strategy is to create a standaolne monolithic Dockerfile, simultanerously researching on the docker-compose implementation.

If a single Dockerfile can withstand the whole technology stack without giving errors then that will be the best case here.

#Usage Example

Using only the single Dockerfile contianer
```Bash
docker run -v <PWD>:<Base> -it image-name
```

A docker-compose.yml example
```Bash
ractome:
  image: reactome
  volumes:
   - <PWD>:/
  links:
   - mysql:db
  environment:
   - any environment variables
  restart: always

mysql:
  image: mysql
  volumes:
  - <PWD>:/home/postgres
  environment:
  - Any variables
  restart: always
```

with this, we can setup reactome.
