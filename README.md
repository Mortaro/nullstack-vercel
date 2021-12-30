# Nullstack Vercel

<img src='https://raw.githubusercontent.com/nullstack/nullstack/master/nullstack.png' height='60' alt='Nullstack' />

## How to deploy SSR on Vercel

Create `api/nullstack.js` to export the production application server

```js
import application from '../.production/server'

export default application.server;
```

Add the following `vercel.json` to the root folder in order to redirect all requests to nullstack:

```json
{
  "version": 2,
  "functions": {
    "api/nullstack.js": {
      "includeFiles": ".production/**"
    }
  },
  "routes": [
    {
      "handle": "filesystem"
    },
    {
      "src": "(.*)",
      "dest": "api/nullstack.js"
    }
  ]
}
```

Rename `build` to `vercel-build` in package.json scripts

```json
  "scripts": {
    "start": "npx nullstack start",
    "vercel-build": "npx nullstack build --mode=ssr"
  }
```

## How to run this Project

Install the dependencies:

`npm install`

Copy the environment sample to a .env file

```sh
NULLSTACK_PROJECT_NAME="[dev] Nullstack Vercel"
NULLSTACK_PROJECT_DOMAIN="localhost"
NULLSTACK_PROJECT_COLOR="#D22365"
NULLSTACK_SERVER_PORT="5000"
```

Run the app in development mode:

`npm start`

Open [http://localhost:5000](http://localhost:5000) to view it in the browser.

## Learn more about Nullstack

[Read the documentation](https://nullstack.app/documentation)