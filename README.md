version: '3'

services:
  db:
    image: postgres:latest
    environment:
      POSTGRES_DB: nextcloud
      POSTGRES_USER: nextcloud
      POSTGRES_PASSWORD: securepassword
    volumes:
      - db:/var/lib/postgresql/data

  nextcloud:
    image: nextcloud:latest
    ports:
      - 8080:80
    volumes:
      - nextcloud:/var/www/html
    environment:
      POSTGRES_HOST: db
      POSTGRES_DB: nextcloud
      POSTGRES_USER: nextcloud
      POSTGRES_PASSWORD: securepassword
    depends_on:
      - db

volumes:
  db:
  nextcloud:
