# FlyFast

This repository contains the full source code for the Demo Application.

## Prerequisites

1. Git
2. an Aternity APM account (SaaS)
3. a Docker host, for example [Docker Desktop](https://www.docker.com/products/docker-desktop)

## Step by Step
### 1. Clone and Update Submodules
```
git clone --recurse-submodules https://github.com/Aternity/FlyFast.git
```
### 2. Get your CustomerID & SaaS Analysis Server Host details from the Aternity APM webconsole

Navigate to Aternity APM (for example [https://apm.myaccount.aternity.com](https://apm.myaccount.aternity.com)) > Agents > Install Agents:

1. Find your **CustomerID**, for example *12341234-12341234-13241234*
2. Grab **SaaS Analysis Server Host**, for example *agents.apm.myaccount.aternity.com*

Those information are required to activate the Aternity OpenTelemetry Collector container, passing via the environment variable `SERVER_URL`. 

### 2. Start the containers

Start the containers using the [docker-compose.yml](docker-compose.yml), for example with Bash:

```bash
cd FlyFast

# Configure the environment variables for the Aternity OpenTelemetry Collector
export ATERNITY_SAAS_SERVER_HOST="agents.apm.myaccount.aternity.com"
export ATERNITY_CUSTOMER_ID="12341234-12341234-13241234"

# Build our docker with no cache
docker-compose build --no-cache

# Start the service
docker-compose up
```

or with PowerShell:

```PowerShell
cd FlyFast

# Configure the environement variable for the Aternity OpenTelemetry Collector
$env:ATERNITY_SAAS_SERVER_HOST="agents.apm.myaccount.aternity.com"
$env:ATERNITY_CUSTOMER_ID="12341234-12341234-13241234"

# Build our docker with no cache
docker-compose build --no-cache

# Start the service
docker-compose up
```

### 3. Stop the containers
```
docker-compose stop
```

## Notes
### Updating Based On Future Changes
Stay up to date with the latest changes.
```
git submodule update --remote
```