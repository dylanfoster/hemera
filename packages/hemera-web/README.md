# Hemera-web
Http route mapping for Hemera microservices. Based on [Micro](https://github.com/zeit/micro)

[![npm](https://img.shields.io/npm/v/hemera-web.svg?maxAge=3600)](https://www.npmjs.com/package/hemera-web)
[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](http://standardjs.com)

#### Example

```js
const Hemera = require('nats-hemera')
const nats = require('nats').connect()
const hemeraWeb = require('hemera-web')

const hemera = new Hemera(nats)
hemera.use(hemeraWeb)

hemera.ready(() => {
  hemera.add({
    topic: 'math',
    cmd: 'add'
  }, (req, cb) => {
    cb(null, req.a + req.b)
  })
})
```

#### Try as GET Request
```
http://localhost:3000?topic=math&cmd=add&a1&b=2
```
#### Try as POST Request
```
http://localhost:3000?topic=math&cmd=add

Body:
{
  "a": 1,
  "b": 2
}
```