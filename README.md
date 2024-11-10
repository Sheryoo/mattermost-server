[![npm version](https://badge.fury.io/js/angular2-expandable-list.svg)](https://badge.fury.io/js/angular2-expandable-list)
[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)

# Mattermost-server

> This is a self-hosted server for Mattermost

## Table of contents

- [Mattermost-server](#mattermost-server)
  - [Table of contents](#table-of-contents)
  - [Prerequisites](#prerequisites)
  - [Getting Started](#getting-started)
  - [Installation](#installation)
    - [Clone the repo](#clone-the-repo)
    - [.env file requirements](#env-file-requirements)
    - [Generate required files](#generate-required-files)
  - [Usage](#usage)
    - [Serving the app](#serving-the-app)
  - [Troubleshooting](#troubleshooting)
  - [Built With](#built-with)
  - [Authors](#authors)
  - [License](#license)

## Prerequisites

This project requires [Docker](https://docs.docker.com/engine/install/) and it's really easy to install.
To make sure you have it available on your machine,
try running the following command.

```sh
$ docker -v
Docker version 27.3.1, build ce1223035a
```

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

## Installation

**BEFORE YOU INSTALL:** please read the [prerequisites](#prerequisites)

Start with cloning this repo on your local machine:

### Clone the repo

```sh
git clone https://github.com/Sheryoo/mattermost-server.git
cd mattermost-server
```

### .env file requirements

you must provide copy environment variables from env.example to run the application.

```sh
cp env.example .env
```

### Generate required files

```sh
$ mkdir -p ~/mattermost/volumes/db/var/lib/postgresql/data

$ mkdir -p ~/mattermost/volumes/app/mattermost/{config,data,logs,plugins,client/plugins,bleve-indexes}
```

## Usage

### Serving the app

```sh
$ sudo docker compose -f docker-compose.yml -f docker-compose.without-nginx.yml up
```

## Troubleshooting

1- if the server is working properly but it show:

> Please check connection, Mattermost unreachable. If issue persists, ask administrator to check WebSocket port.

you must open the config.json file and edit this variables

```sh
{
  "ServiceSettings": {
    "SiteURL": "http://localhost:8065",
    "WebsocketURL": "",
    "AllowCorsFrom": "*"
  }
}
```

to open the file you can use the following command

```sh
nano ~/mattermost/volumes/app/mattermost/config/config.json
```

## Built With

- Love ❤️

## Authors

- **Sheryoo0** - _Initial work_ - [Sheryoo](https://github.com/Sheryoo)

See also the list of [contributors](https://github.com/mattermost-server/contributors) who participated in this project.

## License

[MIT License](./LICENSE) © Sheryoo0
