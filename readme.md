# QHAna Docker

This repository contains a Docker Compose file that can be used to run all services that are necessary for QHAna.

## Start

`docker-compose up`

## Using QHAna

Open http://localhost:8080 in a web browser to use the QHAna UI.
Go to the settings and add http://localhost:5005 to the plugin endpoints.


## Build the Documentation

```bash
# build docs
poetry run sphinx-build docs docs/_build

# update docs requirements (run this after every update to poetry.lock!)
poetry export --dev --format requirements.txt --without-hashes --output "./docs/requirements.txt"
```
