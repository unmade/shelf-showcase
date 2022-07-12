# Shelf Showcase

An example of ready-to-run docker-compose for the Shelf App

<img src="https://i.imgur.com/d8mFhAi.png" alt="shelf-main" width="1379" alt="App Preview">

## Quickstart

To start the aplpication simply run:

```bash
docker compose up
```

Then open in your browser:

```bash
http://localhost:8080
```

By default there is a superuser created when you run the project for the first
time with the default credentials:

- username: **admin**
- password: **root**

## Re-indexing existing file in the storage

Sometime it is easier to put lots of file into the storage and then reindex
them instead of manually uploading via web.

In order to do so, first put the files into corresponding user folder in the storage.
For example, if you have a user `admin`, then put files into `./shelf-data/admin`.

After that run the command:

```bash
docker compose exec shelf-back python manage.py reconcile <username>
```
