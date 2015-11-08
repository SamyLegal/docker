# docker alfresco-community-base

Generate a simple docker image of alfresco community in version 5.0.d.
This image contains only the alfresco webapp, no the share and solr webapp.

## Build of image

```
docker build -t alfresco-community-base:5.0.d .
```

## Compose

This repository contains a docker compose file for start two containers, one for alfresco and a second for the database.

```
docker-compose up -d
```