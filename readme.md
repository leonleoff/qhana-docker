# QHAna Docker

This repository contains a Docker Compose file that can be used to run all services that are necessary for QHAna and the user documentation for QHAna.

The user documentation for QHAna can be viewed on [qhana.readthedocs.io](https://qhana.readthedocs.io) [![Documentation Status](https://readthedocs.org/projects/qhana/badge/?version=latest)](https://qhana.readthedocs.io/en/latest/?badge=latest)


## Start

`docker compose up`

If you want to use the [NISQ-Analyzer](https://github.com/UST-QuAntiL/nisq-analyzer) plugin, use `docker compose --profile nisq up`.

### Docker Compose V1 deprecation

Docker Compose V1 and the `docker-compose` command will no longer be supported by the end of June 2023.
`docker compose` (space instead of hyphen) should be used instead.
For more information about the deprecation of Docker Compose V1 see <https://www.docker.com/blog/new-docker-compose-v2-and-v1-deprecation/>.

## Using QHAna

Open http://localhost:8080 in a web browser to use the QHAna UI.


## Proxy configuration

Some QHAna containers contain a proxy that forwards requests to the host machine.
This makes networking easier when some services are running on the host machine and some in containers.
The environment variable `LOCALHOST_PROXY_PORTS` is used to configure which additional ports will be forwarded to the host machine.
You cannot forward ports that are already bound in the container.

The following containers are already configured to forward the specified ports:
- Plugin Runner and worker: 9090 (backend)
- Backend: 5005 (Plugin Runner)
- Registry worker: 5005 (Plugin Runner)

To temporarily add more ports to the proxy configuration, set the environment variable `EXTRA_PROXY_PORTS` to the additional ports e.g. `:1234 :2345`.
This can be done by creating a file named `.env` that contains e.g. `EXTRA_PROXY_PORTS=":1234 :2345"`.


## Waiting for containers to be ready

The qhana-plugin-runner, qhana-backend and qhana-plugin-registry images use `docker-compose-wait` to be able to wait for endpoints in other containers to be ready to receive requests. For configuration options see: https://github.com/ufoscout/docker-compose-wait?tab=readme-ov-file#additional-configuration-options


## Using the docker-compose setup to develop plugins

The docker compose setup can be used together with a locally running plugin runner instance.
This can be useful during plugin development.
To use a local plugin runner instance instead of the docker-compose instance make sure that the `qhana-plugin-runner` and `worker` services are not running before starting the local instance.
Both the plugin runner and its corresponding worker must either run inside the docker-compose setup or locally.
However, they can share the same redis instance, as they use different routing keys by default (can be changed with the `CELERY_QUEUE` env var).


## Build the Documentation

```bash
# build docs
poetry run sphinx-build docs docs/_build

# update docs requirements (run this after every update to poetry.lock!)
poetry export --with dev --format requirements.txt --without-hashes --output "./docs/requirements.txt"
```


## Known Issues

- ufw on linux blocks connections from the backend to the plugin runner
   - temporary fix: open port 5005 in ufw or use firewalld instead of ufw


## Acknowledgements

Current development is supported by the [Federal Ministry for Economic Affairs and Climate Action (BMWK)] as part of the [PlanQK] project (01MK20005N).

   [Federal Ministry for Economic Affairs and Climate Action (BMWK)]: https://www.bmwk.de/EN
   [PlanQK]: https://planqk.de

## Haftungsausschluss

Dies ist ein Forschungsprototyp. Die Haftung für entgangenen Gewinn, Produktionsausfall, Betriebsunterbrechung,
entgangene Nutzungen, Verlust von Daten und Informationen, Finanzierungsaufwendungen sowie sonstige Vermögens- und
Folgeschäden ist, außer in Fällen von grober Fahrlässigkeit, Vorsatz und Personenschäden, ausgeschlossen.

## Disclaimer of Warranty

Unless required by applicable law or agreed to in writing, Licensor provides the Work (and each Contributor provides its
Contributions) on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied, including,
without limitation, any warranties or conditions of TITLE, NON-INFRINGEMENT, MERCHANTABILITY, or FITNESS FOR A
PARTICULAR PURPOSE. You are solely responsible for determining the appropriateness of using or redistributing the Work
and assume any risks associated with Your exercise of permissions under this License.
