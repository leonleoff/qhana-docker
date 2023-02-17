# QHAna Docker

This repository contains a Docker Compose file that can be used to run all services that are necessary for QHAna and the user documentation for QHAna.

The user documentation for QHAna can be viewed on [qhana.readthedocs.io](https://qhana.readthedocs.io) [![Documentation Status](https://readthedocs.org/projects/qhana/badge/?version=latest)](https://qhana.readthedocs.io/en/latest/?badge=latest)


## Start

`docker compose up`

If you want to use the [NISQ-Analyzer](https://github.com/UST-QuAntiL/nisq-analyzer) plugin, use `docker compose --profile nisq up`.

## Using QHAna

Open http://localhost:8080 in a web browser to use the QHAna UI.


## Proxy configuration

To temporarily add more ports to the proxy configuration, set the environment variable `EXTRA_PROXY_PORTS` to the additional ports e.g. `:1234 :2345`.
This can be done by creating a file named `.env` that contains `EXTRA_PROXY_PORTS=":1234 :2345"`.


## Build the Documentation

```bash
# build docs
poetry run sphinx-build docs docs/_build

# update docs requirements (run this after every update to poetry.lock!)
poetry export --dev --format requirements.txt --without-hashes --output "./docs/requirements.txt"
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
