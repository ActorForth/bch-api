# bch-api

[![Greenkeeper badge](https://badges.greenkeeper.io/christroutner/bch-api.svg)](https://greenkeeper.io/)

[![Build Status](https://travis-ci.org/christroutner/bch-api.svg?branch=master)](https://travis-ci.org/christroutner/bch-api)

**Deprecation Warning:** This repository has been moved to the [Permissionless Software Foundation bch-api repository](https://github.com/Permissionless-Software-Foundation/bch-api). This repository is deprecated. [@chris.troutner/bch-api v1.0.0](https://www.npmjs.com/package/@chris.troutner/bch-api) is the last version published from this repository. [@psf/bch-api v1.1.0+](https://github.com/Permissionless-Software-Foundation/bch-api) is the continuation of the library.

This is a fork and alternative implementation of
the [rest.bitcoin.com](https://github.com/Bitcoin-com/rest.bitcoin.com) repository.
The purpose of this code is to create a REST API server that provides a common
interface for working with a Bitcoin Cash full node and various indexers. See [this article](https://troutsblog.com/research/bitcoin-cash/how-to-bch-full-stack-developer) to learn about the 'Cash Stack'. Visit [FullStack.cash](https://fullstack.cash), sign up for a free account, and use this REST API right away with the [bch-js](https://github.com/christroutner/bch-js) JavaScript library.

This repository is intended to be paired with [bch-js](https://github.com/christroutner/bch-js),
an npm JavaScript library, and an alternative implementation
of [BITBOX SDK](https://github.com/Bitcoin-com/bitbox-sdk).

Both bch-api and bch-js are part of the
[full stack of BCH software](https://troutsblog.com/research/bitcoin-cash/how-to-bch-full-stack-developer).

- [API Documentation](https://api.bchjs.cash/docs/)
- [BCH Example Applications](https://github.com/Permissionless-Software-Foundation/bch-js-examples)
- [slp-cli-wallet](https://github.com/christroutner/slp-cli-wallet): a hacker-friendly, command-line BCH and SLP token wallet using this REST API.

Have questions? Need help? Join our community support
[Telegram channel](https://t.me/bch_js_toolkit)

## Features
The following features set this repository apart from rest.bitcoin.com:

- Address balance and UTXO queries use the [Blockbook](https://github.com/trezor/blockbook)
indexer instead of Insight.
- Fine grain access is controlled with a JWT token using
[this back end auth server](https://github.com/Permissionless-Software-Foundation/jwt-bch-api) and [this front end](https://github.com/Permissionless-Software-Foundation/jwt-bch-frontend).
- Default rate limits are set to 3 RPM for anonymous connections, 10 RPM for [free accounts](https://fullstack.cash/pricing), up to 100 RPM if a full-access JWT token is used.
- Typescript removed and ES8 JavaScript used instead.
- npm audit run on all dependencies.
- [Greenkeeper](https://greenkeeper.io/) implemented for automatic dependency management
and security updates.

## Live Demo
You can test a live demo of the REST API by running the
[bch-js examples](https://github.com/Permissionless-Software-Foundation/bch-js-examples).
Rate limits are 3 requests per minute, but you can increase them to 10 with a [free account](https://fullstack.cash/pricing).
This is fast enough to try out the examples
but these servers are not intended as a freemium service. You can run your own
REST server by purchasing the hard drive at [bchjs.cash](https://bchjs.cash).

- Mainnet REST API server: https://api.fullstack.cash/v3/
- Testnet REST API server: https://tapi.fullstack.cash/v3/
- Check server status: https://metrics.fullstack.cash

## Installation
There are two installation paths, depending if you want a *development* or
*production* environment. You'll also need to set up the underlying infrastructure
described [this page](https://troutsblog.com/research/bitcoin-cash/how-to-bch-full-stack-developer).

This code targets the Ubuntu 18.04 LTS Linux OS.

### Development
This is a standard node.js project. The installation is as follows:

- Clone this repository:

`git clone https://github.com/christroutner/bch-api && cd bch-api`

- Install dependencies:

`npm install`

- Customize the [start-dev-example.sh](start-dev-example.sh) shell script to
point to the required infrastructure. Start the bch-api REST API by running
this script:

`./start-dev-example.sh`

### Production
For a production environment, a Docker container is provided in the
[docker](docker) directory. One for mainnet and one for testnet. Again, these
containers target the Ubuntu 18.04 LTS Linux OS.

- Install Docker and Docker Compose by following the commands on
[this Dev Ops page](https://troutsblog.com/research/dev-ops/overview).

- Customize the [bash script](docker/mainnet/start-local-mainnet.sh) for your
installation.

- Build the Docker container with:

`docker-compose build --no-cache`

- Run the Docker container with:

`docker-compose up`

## Support
Have questions? Need help? Join our community support
[Telegram channel](https://t.me/bch_js_toolkit)

## License
[MIT](LICENSE.md)
