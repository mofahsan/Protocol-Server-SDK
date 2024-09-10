# Introduction

The ONDC Protocol Server facilitates the conversion of Beckn payloads to business payloads and vice versa. It also handles schema, attribute and auth validation.

It is config based as it can be used to run any use case with its configuration.

By leveraging the Protocol Server, network participants can seamlessly interact with the ONDC network. It ensures that the data exchanged between buyers and sellers adheres to the specified schema, promoting interoperability and consistency.

# Sub-repo

## Sandox-UI

It is the front end for the protocol server build with react.

## Buyer Mock Engine

A Node.js server that interacts with the front end and handles the business logic for the buyer.

## Seller Mock Engine

A Node.js server that interacts with the front end and handles the business logic for the seller.

## Protocol server Engine

A Node.hs server that interacts with the gateway, create/extraction of beckn payload and handles validation.

## Protocol Server Config

Holds configs for creation/extraction of beckn payload.

## Buyer Mock Config

Holds configs for rendering UI elements and order of transaction for buyer.

## Seller Mock Config

Holds configs for rendering UI elements and order of transaction for seller.

# Prerequisites

- Node.js
- git
- npm
- ngrok (https://ngrok.com/download)

# How to run - local

- Start ngrok instance

For mac :

open terminal and type

```
ngrok http 80
```

For windows:

open the ngrok.exe file, it will open a terminal.

```
ngrok.exe http 80
```

- Clone sandbox ui repo [https://github.com/mofahsan/sandbox-ui]
- Start sandbox ui

```
npm start
```

- Clone buyer mock engine/seller mock engine as per the type of application you want to run.<br />
  [
  buyer mock engine : https://github.com/ONDC-Official/buyer-mock-engine <br />
  seller mock enigne: https://github.com/ONDC-Official/seller-mock-engine
  ]
- Add .env.dev file

```
PORT = 8000
CONFIG_URL = "https://raw.githubusercontent.com/ONDC-Official/buyer-mock-config/FIS-PRMAAN-dev/build/build.json" // github link for pulling the config
PROTOCOL_SERVER_BASE_URL = "http://localhost:80/"  // make sure it is the same port where ngrok instance is up

```

- Start buyer mock engine/seller mock engine

```
npm run dev
```

- Clone protocol server engine [https://github.com/ONDC-Official/protocol-server-engine]
- Add .env file

```
config_url= https://raw.githubusercontent.com/ONDC-Official/protocol-server-config/fix/personal-loan/build/build.json
PORT = 80 // should be the same port where ngrok instance is up
BUSINESS_SERVER_IS_SYNC = false
IS_VERIFY_AUTH = false
SERVER_TYPE = BAP // change based on type of protocol server: BAP for buyer, BPP for seller
SUBSCRIBER_URL = https://ghost-driving-sunfish.ngrok-free.app // ngrock url
BACKEND_SERVER_URL= http://localhost:8000 // url for buyer/seller mock engine
GATEWAY_URL = "https://staging.gateway.proteantech.in/"
PRIVATE_KEY=<---PRIVATE KEY--->
SUBSCRIBER_ID=<---SUBSCRIBER ID--->
SUBSCRIBER_UNIQUE_KEY=<---SUBSCRIBER UNIQUE KEY--->
is_loadConfigFromGit = true

DATABASE_CONNECTION_STRING = mongodb://localhost:27017/protocolServerBAP
USE_DB = false
VERSION = 1.0.0
```

- Start protocol server engine

```
npm run dev
```
