# NoPress

NoPress makes life easier for both site-developers and copntent-editors by decoupling the WP backend from the client-aplication. 
By introducing a middlelayer of cached WP output in JSON format, it improves the development-process, maintenance and overall performance.

### Prerequisites

You need to have [node](https://nodejs.org/en/)^5.3.*, [docker](https://www.docker.com) and [docker-compose](https://docs.docker.com/compose/install/) installed


### Installing

Clone this repo with `--reursive` to get all the submodules cloned, as well.

```
git clone --recursive git@github.com:radu-m/no-press.git
```

Otherwise your WP installation will be the one from within the official WP docker image.

From within the cloned repo, do

```
docker-compose up -d
```

This should take care of setting up the WP installation.

If everything worked, go to your browser and navigate to `0.0.0.0:8080`. You should see the WP installation screen. If it didn't work, check the state of the containers with:

```
docker ps -a
```

Sometimes the WP container fails and exits on the first run. In this case, simply rerun previous command.

This will create a fresh WP instance, and you will have to install it from scratch.

### WP
If the browser 404's on you, don't panic.
Keep calm and check the state of your containers.
If the container is alright, keep refreshing/reopening the tab. It needs some time to wake up... Otherwise, you're on your own {-_-}

If you'd like to run a everything as **quick** as possible, I suggest you first skip to the PHPMyAdmin part and import the example DB, which will save you quite some work. 

Alternatively, if you intend to start from the very beginning:
* after signing into WP, go to `plugins` and `activate` all of them.
* go to `Settings -> Permalinks` and set it to `Post name` and don't forget - Jesus saves ;)
* go to `Settings -> JSON API` and `enable` all of the controllers.
* There's a box at the top of the content-area, with 3 buttons. Coose to set up WPML so it exposes at least 1 language. NoPress is coupled with WPML, for now. Just leave the vanilla settings and click next/remind me later

### DB 

For persistence, the DB will be stored under `/db-wp`. Will eventually improve this flow...
You can find the DB credentials within `no-press-wp/wp-config.php

usr: `root`
pwd: `example`

...obviously, changing them is on you.

**recommended:**
You can also use PHPMyAdmin to import the .sql file from ./no-press-wp, so you won't have to manually set up the WP installation, activate plugins, create example post, yadda-yadda.

usr: `radium`
pwd: `admin`

### PHPMyAdmin
In your browser, go to 0.0.0.0:8081 and you shall find the auth-screen
In your terminal, do 

```
docker ps -a
```

and copy the ID of your `mysql:*` container. Use this ID as the server name requested by phpMyAdmin.

usr: `root`
pwd: `example`

If you'd like to import the example DB mentioned above, you need to manually create a DB named `wordpress` [if it's not there], select it and then import the `.sql.gz` file from under the 'import' tab.

### CLIENT

## no-press-angular

AngularJS client with hello-world application.


`cd` into `./no-press-angular` and do

```
npm install
```

Assuming all went well, now you can start the dev server by doing

```
npm run dev
```

..that's it! Webpack should have opened a new tab and shall be watching over your files.


If you have any problems with running any of this, please raise an issue

## Happy dev!
