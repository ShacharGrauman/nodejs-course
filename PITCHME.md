---?image=assets/images/grauman-at-wobi.png

---
# Introduction

Our Facebook Group: 
GRAUMAN- Node.Js at WOBI

WhatsApp:
https://chat.whatsapp.com/HiWZtxYZU0WF0Q9geUFxYD

Tools: 
VSCode, Browser

---

## Node.js @ Wobi

@color[#e49436](GRAUMAN) dev courses for R&D teams
https://www.grauman.co.il

---
#### @color[#e49436](Express)

`> npm init -y`

`> npm install express --save`

```js
const express = require('express');
```
Which returns a function...

---
#### @color[#e49436](Express)

```js
const express = require('express');
const app = express();
```
Which is a server like we did before
```js
//Inside Express code
app.listen = function listen() {
  var server = http.createServer(this);
  return server.listen.apply(server, arguments);
};
```

---
#### @color[#e49436](Express)

```js
const express = require('express');
const port = process.env.PORT || 3100;
const app = express();

app.listen(port, 
    () => console.log(`Server listening on port ${port}`));

```
So we can listen for incoming request on some port

---
#### @color[#e49436](Express)

Express exposes HTTP methods more easily

```js
//...
const app = express();

app.get('/', (req, res) => {
    res.send('Ahalan');
});

app.listen(port);
```
So we can listen for incoming request on some port

---
#### @color[#e49436](Express) Status Codes

```js
res.sendStatus(200); // res.status(200).send('OK')
res.sendStatus(403); // res.status(403).send('Forbidden')
res.sendStatus(404); // res.status(404).send('Not Found')
res.sendStatus(500); // res.status(500).send('Internal Server Error')
```
---
#### @color[#e49436](Express) Responses Types

Express intercepts, to some extent, the content of my response

```js
//...
app.get('/html', (req, res) => {
    res.send(`<html><head></head>
    <body>
        <h1>Ahalan Express!</h1>
        <h2>I'm an HTML</h2>
    </body></html>`);
});

```
So we can respond more descriptively

---
#### @color[#e49436](Express) Responses Types

```js
//...

app.get('/json', (req, res) => {
    res.json({nama: 'Shahar', age: 27});
});

//...
app.get('/download', (req, res) => {
    res.download(path.join(__dirname, '../files/somePDF.pdf'));
});

```

---
#### @color[#e49436](Express) nodemon

We can install nodemon for watching file changes 

It will reload our server automatically

`> npm install -g nodemon`

---
#### @color[#e49436](Express) Route paths

```js
app.get('/ahalan/:name', (req, res) => {
    res.send(`<html><head></head><body>
        <h1>Ahalan ${req.params.name}</h1>
    </body></html>`);
});

app.get('/aha?lan/:name', function (req, res) {
    res.send(`<html><head></head><body>
        <h1>Ahalan ${req.params.name}</h1>
    </body></html>`);
});
//ahalan, ahlan
```

---
#### @color[#e49436](Express) Route paths

```js
app.get('/ahala+n/:name', function (req, res) {
  res.send(`<html><head></head><body>
        <h1>Ahalan ${req.params.name}</h1>
    </body></html>`);
});
//ahalan, ahalaan, ahalaaaaan etc.

app.get('/ahala*n/:name', function (req, res) {
  res.send(`<html><head></head><body>
        <h1>Ahalan ${req.params.name}</h1>
    </body></html>`);
});
//ahalan, ahalaaan, ahalabcdn etc.
```

---
#### @color[#e49436](Express) Route paths

```js
app.get(/.*lan$/, function (req, res) {
  res.send(`<html><head></head><body>
        <h1>Ahalan!</h1>
    </body></html>`);
});
//ahalan, kablan
//Not ahalanyo etc.
```

---
#### @color[#e49436](Express) Static files

Whenever we need to serve static files (HTML, CSS, JSON, Images, Files...)

We tell Express to *use* our assets folder

```js
app.use('/content', express.static(path.join(__dirname, 'assets'));
//...
app.get('/html', (req, res) => {
    res.send(`<html><head>
    <link href='content/styles.css' type='text/css' rel='stylesheet' />
    </head>
    <body><h1>Ahalan Express!</h1>
    </body></html>`);
});
```

---
#### @color[#e49436](Express) Middleware

We've just used middleware

Middleware sits between the request and the response:

- Execute some code
- Perform changes on request / response objects
- Decide to end the request-response cycle
- Continue to the next middleware

---
#### @color[#e49436](Express) Middleware

```js
app.use('/', (req, res, next) => {
    console.log(`Incoming request: ${req.url}`);
    next();
});
```

---


