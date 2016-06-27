# L10n Translation Database

This repo holds the Docker configurations required to setup the L10n Translation Database and WUI. The Database is MySQL and the Web application is [L10n](https://github.com/bvanderlaan/website-l10n)

The L10n Translation Database Site is setup using Docker; that is there is a single host machine which hosts multiple Docker containers. Two of the Docker containers being hosted are the **l10n** and **l10ndb** containers.

The *l10n* container is created via the *ruby* image from http://hub.docker.com and is the container which is hosting L10n (a translation database web application).

The *l10ndb* container is created via the *mysql* image from http://hub.docker.com and is the container which hosts the database which is used by the installation of L10n.

# Install Docker
The first thing you will need to do is install Docker on your host machine. To do this follow the instructions found here: https://docs.docker.com/engine/installation/

# Install Docker Compose
The L10n Translation Database site is setup as a service, that is we are creating a service for our users to use but internally the service is
constructed by networking together multiple containers. This can be done with Dockerfiles and bash scripts but there is a tool called
Docker Compose which allows you to define a service via a YMAL file. To use this tool you first need to install it; to do that follow these instructions: https://docs.docker.com/compose/install/

# Start the Service
To start the L10n Translation Database service using Docker Compose navigate into the folder where the docker-compose.yml file exists then run the following command:

```
me@pc$ docker-compose up
```

This will pull the needed images then create and start the l10n and l10ndb containers.

At this point you can access the L10n site via the host machine on port 8282 such as: http://localhost:8282

The above command will run the containers in attached mode, that means all the logs generated will be displayed in your terminal.
This also means you can no longer use your terminal. To stop the container type *Ctrl+C*. To execute the containers in detached mode, that is have them run in the background use the following command:

```
me@pc$ docker-compose up -d
```

You can see what containers are running by typing

```
me@pc$ docker-compose ps
```

# Shutting Down the Service

If you run the continers in detached mode in order to stop them use the following command:

```
me@pc$ docker-compose down
```

# Rebuilding the Service

To rebuild the L10n image defined in your docker-compose.yml file use the following command:

```
me@pc$ docker-compose build --no-cache
```

Make sure the services is no running when you run the above command. This will re-create the image which in this case will download the latest version of the webapp. It will then re-create the containers. 
To start them up again follow the *Start the Service* instructions above.