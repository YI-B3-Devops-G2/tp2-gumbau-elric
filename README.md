<p align="center">
  <a href="https://example.com/">
    <img src="https://pbs.twimg.com/profile_images/979714483387092994/PMI-aUXp_400x400.jpg" alt="Logo" width=85 height=85>
  </a>

  <h3 align="center">Ynov - B3 Info - GUMBAU Elric</h3>
</p>

## B3 Devops - TP 2

- [About me](#About-me)
- [About this project](#About-this-project)
- [Prerequisites](#Prerequisites)
- [What's included](#whats-included)
- [How its work ?](#whats-included)
- [Containers and networks](#Containers-and-networks)
- [How to install ?](#Containers-and-networks)
- [Check if it's functional](#Check-if-its-functional)
- [How to check ?](#Check-if-its-functional)
- [How to stop ?](#Docs)
- [Docs](#Docs)


## About me

About me

- elric.gumbau@ynov.com (mail)
- [GUMBAUElric](https://github.com/GUMBAUElric) (github)
- [GUMBAU Elric](https://fr.linkedin.com/in/elric-gumbau-30943417a/) (linkedIn)

## About this project

Using a docker-compose.yml, an nginx, nodejs, redis and postgres infrastructure is created.

## Prerequisites

Here are the prerequisites necessary for this project
     
   |     Prerequisites      |         
   | ---------------------- |
   |         Docker         |      
   |         Node.js        |   

    > Ask google how to install these tools if you don't have them 😉

## What's included

```text
tp2-gumbau-elric/
└── Docker/
    ├── docker-nginx/
    │   ├── default.conf
    │   └── Dockerfile
    ├── docker-nodejs/
    │   ├── Dockerfile
    ├── docker-compose.yml
└── .dockerignore
└── CHANGELOG.md
└── package.json
└── README.md
└── server.js
```

## How its work ?

Nginx allows to make a proxy pass on the node server which requests redis and postgres in order to display the following messages.

- GET /api

      { "message": "Hello World" }

- GET /api/status

      {"status": "OK", "postgresUptime": String, "redisConnectedClients": Number}

When you type http://localhost:3000 this redirects to the node server listening on port 3000. 

Check file in Docker/docker-nginx/default.conf.


## Containers and networks

- 4 containers and 2 networks are created, alpine linux distribution are use

    |      Containers       |        Distrib         |
    |-----------------------|------------------------|
    | docker_docker-nginx_1 |      alpine_1.17.6     |
    | docker-tp-nodejs      |      alpine_13.3       |
    | docker-tp-postgres    |                        |         
    | docker-tp-redis       |                        |

    |        Networks        |         
    |------------------------|
    | docker_network-nodejs  |      
    |   docker_network-db    |

## How to install ?

- Clone this git repo and place it anywhere on your pc

- Open a terminal, go to the folder 'tp2-gumbau-elric' and type
    
      npm install
      cd Docker/
      docker-compose up

> 'npm install' install all the node_modules

> 'docker compose up' allows to "build" the infrastructure and create our 4 containers and 2 networks (to learn more about the docker compose check the docs section)

> it may take a while, be patient ! 👍

If you see the following two lines on the terminal

      docker-tp-nodejs   | Connected to database tpdocker !
      docker-tp-nodejs   | Server listen on port 3000 !

that mean that all the infrastructure is operational !

Well done !

## Check if it's functional

- Open a web browser and type the url

      http://localhost:3000/api

- Normally this returns the following result

      {"message":"Hello World"}


- Same thing for the following url

      http://localhost:3000/api/status

- Result 

      {"status":"ok","postgresUptime":"Xm Xs","redisConnectedClients":X}

If you have the same results, it means that you have installed the infrastructure perfectly !

Well done !

## How to check ?

- If you want to check that our 4 containers have been created and are running, type this command in the terminal

      docker ps

If you see that on NAMES section

      NAMES
      docker_docker-nginx_1
      docker-tp-nodejs
      docker-tp-postgres
      docker-tp-redis

that means that the 4 containers are running !

- If you want to check that our 2 networks have been created and are running, type this command in the terminal

      docker network ls

If you see that on NAME section

      NAME
      docker_network-db
      docker_network-nodejs

that means that the 2 networks are running !

## How to stop ?

- Open a terminal, go to the folder 'tp2-gumbau-elric' and type

      cd Docker
      docker-compose down

> 'docker compose down' allows to "Stops and removes " our 4 containers and 2 networks, chek with 'docker ps' and 'docker network ls' to be sure. (For more infos, check docs section)

## Docs

Docker              : https://docs.docker.com/

Dockerfile          : https://docs.docker.com/engine/reference/builder/

Docker compose      : https://docs.docker.com/compose/

Docker compose up   : https://docs.docker.com/compose/reference/up/

Docker compose down : https://docs.docker.com/compose/reference/down/

Alpine              : https://alpinelinux.org/

Node.js              : https://nodejs.org/en/


Enjoy ! 😉
