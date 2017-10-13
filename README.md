# git-wordpress

Version control scheme to enable collaboration on a WordPress project.

## Requirements

* [Docker Engine](https://docs.docker.com/compose/install/)

* [Docker Compose](https://docs.docker.com/engine/installation/)

* [Manage Docker as a non-root user](https://docs.docker.com/engine/installation/linux/linux-postinstall/)

  * Alternatively, you can map `wordpress` service to port >1024 in `docker-compose.yml` and `environment.env`.

## Setup

Clone this repository and change directory into it

`docker-compose up`

Running this command will populate your repository with the latest version of
wordpress.

Browse to `localhost`, you should see installation instructions

If you see

> Error establishing a database connection.

Then, wait until mysql container loads and try again.

|                   |               |
|-------------------|---------------|
| **Database Name** | *my_database* |
| **Username**      | *my_user*     |
| **Password**      | *123*         |
| **Database Host** | *my-mysql*    |

Values are configurable from `docker-compose.yml` and `environment.env` (*requires `docker-compose restart`*).

If you see

> Sorry, but I can’t write the wp-config.php file.

Then, run `docker-compose restart` and try again.

Run `bash docker-mysql-export` to export the database into `database.sql`.

Finally, `git commit -m "Initial commit"`.

## Exporting

`docker-mysql-export [CONTAINER] [DUMP_FILENAME]`

## Importing

`docker-mysql-import [CONTAINER] [DUMP_FILENAME]`

## Compatibility Notes

* Mac `sed` is inconsistent with GNU `sed`
  * [Fix with `brew install gnu-sed --with-default-names`](https://superuser.com/a/582558/558061)