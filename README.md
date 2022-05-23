# moralis-vue-boilerplate
Use this repository as a starting point for Moralis and Vue.js to build up Web3 dApps. I do not added any stylings or anything else, so you could add it by yourself and customize as you prefer.

## Before you start
Please ensure, [you signed up for an account](https://moralis.io) and created a server to obtain the

- application id
- server url

You will need those for creating the environment variables.

```
VUE_APP_MORALIS_APPLICATION_ID=abc123
VUE_APP_MORALIS_SERVER_URL=https://abc123.bigmoralis.com:2053/server
```


## Getting started
```
git clone git@github.com:hypescale/moralis-vue-boilerplate.git

cd moralis-vue-boilerplate

yarn install

yarn serve

### production build
yarn build

### linting
yarn lint
```

## Sponsor
If you think this is useful for you, I am happy if you support this project by a small donation
SOL: FAyNvBBRttbrLiGtW1i1ovH1JC3LifFN15U2qNDgF9FT
ETH: 0xFcb6912A30b79F9FF5fb1b3262A296De0fb2c0A2

## FAQ
**Question:** What is Moralis?

**Answer:** With Moralis you can aggregate many different tools and APIs which works as a glue for them all. With that service you can develop a decentalized app (dApp) which is needed when developing a decentralized app that requires access to the blockchain, like Ethereum or Binance Smart Chain.

[![What is Moralis?](https://img.youtube.com/vi/txHnWDRB728/0.jpg)](https://www.youtube.com/watch?v=txHnWDRB728)

**Question:** Do I need a server to host my dApp?

**Answer:** No. Moralis provides a serverless architecture. You only need to [create an account at moralis.io](https://moralis.io) and register the 

- application id
- server url

that's all.

**Question:** My app is not working

**Answer:** Please makes sure, you have created an environment file (.env). If you have created one, make sure, the file ending matches the corresponding environment where you application is running, e.g. local development or production:

- .env
- .env.local
- .env.production


### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
