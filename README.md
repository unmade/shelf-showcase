# Shelf Showcase

An example of ready-to-run docker-compose for the Shelf App

![App Preview Light Theme](https://i.imgur.com/N6QwN94.png)

![App Preview Dark Theme](https://i.imgur.com/m91ZoKF.png)

## Quickstart

To start the application simply run:

```bash
docker compose up
```

Then open it in your browser:

```bash
http://localhost:8080
```

> If you're running it on the remote machine consider to update `API_BASE_URL`
> in the [docker-compose.yml](./docker-compose.yml) from localhost to the LAN IP
> of your docker host.

By default there is a superuser created when you run the project for the first
time with the default credentials:

- username: **admin**
- password: **root**

You can find more in the following repo:

- [https://github.com/unmade/shelf-back](https://github.com/unmade/shelf-back)
- [https://github.com/unmade/shelf-front](https://github.com/unmade/shelf-front)

## Re-indexing existing file in the storage

Sometime it is easier to put all your files into the storage and then reindex
them instead of manually uploading via web.

In order to do so, first put the files into corresponding user folder in the storage.
For example, if you have a user `admin`, then put files into `./shelf-data/admin`.

After that run the command:

```bash
docker compose exec shelf-back python manage.py reindex <username>
docker compose exec shelf-back python manage.py reindex-content <username>
```

The first command will simply add all files in the storage to the database, so
you'll see them on the UI as soon as possible.

The second command extract some metadata, such as EXIF, from target files. It
can take some, especially if you have lots of media files.
