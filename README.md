# logio-server
Logio-Server docker image built on Alpine Linux NodeJS image from https://github.com/mhart/alpine-node

# Usage
`docker run -d -p 28777:28777 -p 28778:28778 -v ${host_config_folder}:/home/logio/.log.io -v ${host_cert_folder}:/cert --name logio-server minzhang/logio-server`

# Configuration
- `log_server.conf` in `${host_config_folder}`
```
exports.config = {
  host: '0.0.0.0',
  port: 28777
}
```
- `web_server.conf` in `${host_config_folder}`
```
exports.config = {
  host: '0.0.0.0',
  port: 28778,

  /* 
  // Enable HTTP Basic Authentication
  auth: {
    user: "admin",
    pass: "admin"
  },
  */

  /* 
  // Enable HTTPS/SSL
  ssl: {
    key: '/cert/ekey.pem',
    cert: '/cert/certificate.pem'
  },
  */

  /*
  // Restrict access to websocket (socket.io)
  // Uses socket.io 'origins' syntax
  restrictSocket: '*:*',
  */

  /*
  // Restrict access to http server (express)
  restrictHTTP: [
    "192.168.29.39",
    "10.0.*"
  ]
  */
}
```

## Note
The `-v ${host_cert_folder}:/cert` parameter is OPTIONAL. Only apply it when needed
