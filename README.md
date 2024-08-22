# Description

This role provisions a [mev-boost](https://github.com/flashbots/mev-boost) installation that can act as a payload builder for ETH2 nodes.

# Introduction

The role will:

* Start a node by defining a [Docker Compose](https://docs.docker.com/compose/compose-application-model/)
* Setup Consul service with checks

# Ports

The service exposes this ports by default:

* `18550` - Prometheus metrics port. Should not be public.

# Installation

Add to your `requirements.yml` file:

```yaml
- name: infra-role-mev-boost
  src: git+git@github.com:status-im/infra-role-mev-boost.git
  scm: git
```

# Configuration

The crucial settings are:

```yaml
mev_boost_network: 'holesky'
mev_boost_relays:
  - 'https://0xaa58208899c6105603b74396734a6263cc7d947f444f396a90f7b7d3e65d102aec7e5e5291b27e08d02c50a050825c2f@holesky.titanrelay.xyz'
```

# Management

## Service

Manged by `docker-compose`:

```sh
docker-compose start
docker-compose stop
docker-compose restart
```

You can view logs with `docker`:

```sh
docker logs mev-boost
```

# Links

- https://docs.flashbots.net/flashbots-mev-boost/introduction
- https://ethstaker.cc/mev-relay-list
