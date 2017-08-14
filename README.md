# NoPress

NoPress is a dev-stack for WordPress that decouples the WP-admin from the client-code, allowing development of multiple clients for the same 'theme'.

### Prerequisites

You need to have [node](https://nodejs.org/en/), [docker](https://www.docker.com) and [docker-compose](https://docs.docker.com/compose/install/) installed


### Installing

**important** Clone this repo with `--reursive` to get all the submodules cloned, as well.

```
git clone --recursive git@github.com:radu-m/no-press.git
```

this is [why](https://stackoverflow.com/questions/3796927/how-to-git-clone-including-submodules)

Otherwise your WP installation will be the one from within the official WP docker image.

From within the cloned repo, do

```
docker-compose up -d
```

This should take care of setting up the WP installation. I've included PHPMyAdmin, as well - remove it from the `docker-copose.yml` if it's not necessary.

If everything worked, go to your browser and navigate to `0.0.0.0:8080`. You should see the WP installation screen.

This will create a fresh WP instance, nd you will have to install it from scratch. For persistence, the DB will be stored under `/db-wp`. Will eventually improve this flow...

### WP
If the browser 404's on you, don't panic.
check the state of your containers with

```
docker ps -a
```

and, if the container is alright, keep refreshing/reopening the tab. It needs some time to wake up...

Otherwise, you're on your own -_-

First thing after signing into WP, go to `plugins` and `activate` all of them.
Second, go to `Settings -> Permalinks` and set it to `Post name`.
Once that's taken care of, go to `Settings -> JSON API` and `enable` all of the controllers.
Finally, set up WPML so it exposes at least 1 language. NoPress code and data-structure is coupled with WPML, for now. Just leave the vanilla settings and click next/remind me later

### DB 

You can find the DB credentials within `no-press-wp/wp-config.php

usr: `root`
pwd: `example`

...obviously, changing them is on you.


### Connecting phpMyAdmin
In your terminal, do 

'''
docker ps -a
'''

and copy the ID of your `mysql:*` container. Use this ID as the server name requested by phpMyAdmin.


### NB

To run the client, follow the steps in the [client repo](https://github.com/radu-m/no-press-angular)
