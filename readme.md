# QHAna Docker

This repository contains a Docker Compose file that can be used to run all services that are necessary for QHAna.

## Start

1. Automatically clone the repositories of the services and build the images with this command:
`docker-compose build`

2. Start all services:
`docker-compose up`

## Open the UI

Open http://localhost:4200 in a web browser to use the QHAna UI.

## Troubleshooting

### "Port 5000 already in use" on Mac OS Monterey
Disable AirPlay Receiver in the system settings.
