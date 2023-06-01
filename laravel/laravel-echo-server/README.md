# Laravel Echo Server

## `laravel-echo-server.json`

須注意 `authHost` 與 `authEndpoint` 連接在一起是正確的 URI。

```json
{
  // 以下 2 種情況是正確的
  // #1
  "authHost": "http://127.0.0.1:8003",
  "authEndpoint": "/broadcasting/auth",
  // #2
  "authHost": "http://127.0.0.1:8003/",
  "authEndpoint": "broadcasting/auth",
  // 以下情況則會導致錯誤
  "authHost": "http://127.0.0.1:8003",
  "authEndpoint": "broadcasting/auth",

  "clients": [],
  "database": "redis",
  "databaseConfig": {
    "redis": {
      "port": "6382",
      "host": "127.0.0.1"
    },
    "sqlite": {
      "databasePath": "/database/laravel-echo-server.sqlite"
    }
  },
  "devMode": true,
  "host": null,
  "port": "6001",
  "protocol": "http",
  "socketio": {
    "cors": {
      "origin": [
        "http://10.34.0.34:8003"
      ]
    }
  },
  "sslCertPath": "",
  "sslKeyPath": "",
  "sslCertChainPath": "",
  "sslPassphrase": "",
  "subscribers": {
    "http": true,
    "redis": true
  },
  "apiOriginAllow": {
    "allowCors": true,
    "allowOrigin": "",
    "allowMethods": "",
    "allowHeaders": ""
  }
}
```
