## Local environment setup (Docker & Laravel)

- Have Docker and Docker compose installed
- Clone this repo and switch to repo directory
	- `git clone git@bitbucket.org:elearningincreaseyourskills/mvp_docker_compose.git`
	- `cd mvp_docker_compose`
- Clone Laravel app into src directory
	- `git clone git@bitbucket.org:elearningincreaseyourskills/mvp.git src`
- Migrations etc
	- run `docker-compose up -d --build site`
	- run `docker-compose run --rm composer update`
	- run `docker-compose run --rm npm run dev`
	- run `docker-compose run --rm artisan migrate` 

- Visit http://localhost:8080/  ... et voilà!



### Persistent MySQL Storage

By default, whenever you bring down the Docker network, your MySQL data will be removed after the containers are destroyed. If you would like to have persistent data that remains after bringing containers down and back up, do the following:

1. Create a `mysql` folder in the project root, alongside the `nginx` and `src` folders.
2. Under the mysql service in your `docker-compose.yml` file, add the following lines:

```
volumes:
  - ./mysql:/var/lib/mysql
```