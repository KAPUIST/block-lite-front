# ethereum-lite-explorer-frontend

## Description

This project is an open-source block explorer on EVM chain. If you follow this repository, you can run explorer in localhost. This repository provides [crawling code](https://github.com/Generation-Foundation/ethereum-lite-explorer-crawling) and [backend code](https://github.com/Generation-Foundation/ethereum-lite-explorer-back) for Explorer, and you can find frontend code in this repository.

## Preview

<img width="800" alt="image" src="https://user-images.githubusercontent.com/93761302/208592091-dd02cd8d-2962-4362-b070-f4397db626d5.png">
<img width="800" alt="image" src="https://user-images.githubusercontent.com/93761302/208592404-dc90629a-72e0-4629-8ab0-b624b2c1ed68.png">
<img width="800" alt="image" src="https://user-images.githubusercontent.com/93761302/208592500-f9ff0923-e5ca-47bc-93f9-dc3aa13f402e.png">

## Getting Started

### Setting up Server

- **Go to the link below to set up server step by step.**
- First, set up Crawling server and Database
  - <https://github.com/Generation-Foundation/ethereum-lite-explorer-crawling>
- Second, set up Backend server
  - <https://github.com/Generation-Foundation/ethereum-lite-explorer-back>

### Installing

**After the above server installation is complete, install the following tasks**

- Git clone this repo

```bash
git clone https://github.com/Generation-Foundation/ethereum-lite-explorer-front.git
```

- **On macOS and Ubuntu**, create `.env` to set GENERATE_SOURCEMAP

```env
GENERATE_SOURCEMAP=false
```

- **On Window**, modify `package.json` to set GENERATE_SOURCEMAP

```javascript
  "scripts": {
    "start": ""set \"GENERATE_SOURCEMAP=false\" && node scripts/start.js",
    "build": ""set \"GENERATE_SOURCEMAP=false\" && node scripts/build.js",
    "test": "node scripts/test.js"
  },
```

- Modify 'baseURL' in `/src/redux/reducer/etherApi.js` to your blockchain RPC URL

```javascript
import axios from 'axios';

const etherApi = axios.create({
  //change your blockchain rpc url
  baseURL: 'https://eth.public-rpc.com',
  //baseURL : "https://testnet-rpc-seoul.gen.foundation",
  headers: { 'content-type': 'application/json' },
});

export default etherApi;
```

- Modify 'baseURL' in `/src/redux/reducer/dbApi.js` to your backend server

```javascript
import axios from 'axios';

const dbApi = axios.create({
  //change your backend server
  baseURL: 'http://localhost:3001',
  headers: { 'content-type': 'application/json' },
});

export default dbApi;
```

- Run it local with the following command

```bash
npm install --save
npm start
```

### Deploy

Deployed using AWS amplify.

```bash
npm run build
```

### Architecture

**If running only on localhost, it will proceed on the following ports.**

- Front - http://localhost:3000
- Back - http://localhost:3001
- Crawling - http://localhost:3006
