# NoPress

NoPress is a dev-stack for WordPress that decouples the WP-admin from the client-code, allowing development of multiple clients for the same 'theme'.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

You need to have [node](https://nodejs.org/en/), [docker](https://www.docker.com) and [docker-compose](https://docs.docker.com/compose/install/) installed


### Installing

From within the cloned repo, do

```
docker-compose up -d
```

This should take care of setting up the WP installation. I've included PHPMyAdmin, as well - remove it from the `docker-copose.yml` if it's not necessary.

If everything worked, go to your browser and navigate to `0.0.0.0:8080`. You should see the WP installation screen.

### NB

To run the client, follow the steps in the [client repo](https://github.com/radu-m/no-press-angular)

This will create a fresh WP instance, nd you will have to install it from scratch. For persistence, the DB will be stored under `/db-wp`. Will eventually improve this flow...