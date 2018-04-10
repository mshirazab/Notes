# Synchronization

This shows how to get nodeJS and react up and going.

## Combining Express app and react

* Install concurrently
  `yarn add concurrently --dev`
* add in package.json in server directory
  ```json
  {
    "scripts": {
      "server": "node server.js",
      "client": "npm start server --prefix client",
      "dev": "concurrently \"npm run server\" \"npm run client\""
    }
  }
  ```
* add in package.json in client directory
  ```json
  {
    "proxy": {
      "/auth/google": "http://localhost:5000"
    }
  }
  ```
