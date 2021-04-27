# docker-compose-laravel
A pretty simplified Docker Compose workflow that sets up a LEMP network of containers for local Laravel development.


## Usage

To get started, make sure you have Docker and docker-compose on your system, and then clone this repository.

Next, navigate in your terminal to the directory you cloned this, and spin up the containers for the web server by running
 
 `docker-compose up -d --build site`.

After that completes, follow the steps from the [src/](src/) file to get your Laravel project added in (or create a new blank one).

Bringing up the Docker Compose network with `site` instead of just using `up`, ensures that only our site's containers are brought up at the start, instead of all of the command containers as well. The following are built for our web server, with their exposed ports detailed:

- **nginx** - `:80`
- **mysql** - `:3306`
- **php** - `:9000`
- **redis** - `:6379`
- **mailhog** - `:8025` 

Three additional containers are included that handle Composer, NPM, and Artisan commands *without* having to have these platforms installed on your local computer. Use the following command examples from your project root, modifying them to fit your particular use case.

- `docker-compose run --rm composer install`
- `docker-compose run --rm artisan migrate` 
- `docker-compose run --rm artisan db-seed` 
