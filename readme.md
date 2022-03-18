# QHAna Docker

This repository contains a Docker Compose file that can be used to run all services that are necessary for QHAna and the user documentation for QHAna.

The user documentation for QHAna can be viewed on [qhana.readthedocs.io](https://qhana.readthedocs.io) [![Documentation Status](https://readthedocs.org/projects/qhana/badge/?version=latest)](https://qhana.readthedocs.io/en/latest/?badge=latest)


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
