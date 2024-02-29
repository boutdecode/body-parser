# Body parser tools by Bout de code

![https://boutdecode.fr](https://boutdecode.fr/img/logo.png)

[Bout de code](https://boutdecode.fr) - Développement de site internet et blog avec de vrais morceaux de codes, simples, élégants, utiles (parfois) et surtout sans fioriture.

## Installation

```shell
$ npm install @boutdecode/body-parser
```

## Yion plugin

For yion : 

```javascript
const { createApp, createServer } = require('@boutdecode/yion')
const bodyParser = require('@boutdecode/body-parser')

const app = createApp()
const server = createServer(app)

app.use(bodyParser())

app.get('/', (req, res) => {
  res.set('Content-Type', 'text/html; charset=utf-8')
    .send(`
      <form action="/file" method="post" enctype="multipart/form-data">
        <input type="file" name="file">
        <input type="submit">
      </form>
    `)
})

app.post('/file', (req, res) => {
  const file = req.body.file // file sent with name "file"
  res.sendFile(file.filepath, file.filename, file.mimetype)
})

server.listen(8080)
```

## Tests

```shell
$ npm run test
```
