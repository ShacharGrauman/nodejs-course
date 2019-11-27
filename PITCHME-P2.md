---?image=assets/images/grauman-at-experis.png

---
# Introduction

Our Facebook Group: 
GRAUMAN- Node.Js at Experis

WhatsApp:
https://chat.whatsapp.com/HiWZtxYZU0WF0Q9geUFxYD

Tools: 
VSCode, Browser

---

## Node.js @ Experis

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
    res.download(path.join(__dirname, 'file.pdf'));
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
app.use('/content', 
        express.static(path.join(__dirname, 'assets'));
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
Which means: Any request starts with '/' will first run through this middleware

---
#### @color[#e49436](Express) Middleware

We can use a much powerfull middleware named *morgan*

`> npm install morgan --save`

```js
const morgan = require('morgan');
//stdout
app.use(morgan('combined')); 

//Or to a file
const logFile = fs.createWriteStream(
    path.join(__dirname, 'logger.log'), 
    { flags: 'a'});

app.use(morgan('combined', { stream: logFile }));

```

---
#### @color[#e49436](Express) Middleware

We can write middleware which inspect the headers and act accordingly

```js
function compress(req, res, next) {
    if(req.headers['accept-encoding'] && 
       req.headers['accept-encoding'].includes('gzip')){
        const gzip = zlib.createGzip();
        fs.createReadStream(path.join(__dirname, 'file.pdf'))
        .pipe(gzip).pipe(res);
    }else{
        next();
    }
}
app.get('/file', compress, (req, res) => {
    fs.createReadStream(path.join(__dirname, 'file.pdf'))
    .pipe(res);
});
```

---
#### @color[#e49436](Express) Querystring & Post params

```js
request.query //will hold query params
//localhost:3100/users?year=2010 -> req.query.year

request.params //will hold url path params
//localhost:3100/user:id -> req.params.id

request.body //will hold post params
//using body-parser library
```

---
#### @color[#e49436](Express) Template Engine

Template Engine is a way of structuring a page with dynamic content

The page has known placeholders 

We load that file and inject the content into those placeholders

---
#### @color[#e49436](Express) Custom Template Engine

```js
//Provide your engine file extension name
//and function: the file to load, inject data, callback
app.engine('sg', (file, data, cb) => {
    //Read the file, 
    //Inject data as your engine requires
    //Call cb with the result    
}
//Then tell express where to locate 'sg' files
app.set('views', './views'));
//And finally register 'sg' engine
app.set('view engine', 'sg');
```

---
#### @color[#e49436](Express) Custom Template Engine

```js
//render the page using sg engine!
//Pass data object
app.get('/', (req, res) => {
    res.render('index', {
        data1: 'Some data to be injected',
        data2: 'Other data'
        //...
    });
});
```

---
#### @color[#e49436](Express) EJS Template Engine

*ejs* templage engine is a simple templating engine

It uses similar syntax as used in *aspx* pages

`> npm install ejs --save`

---
#### @color[#e49436](Express) EJS Template Engine

Ex - Use ejs as the template engine

Create 2 pages:

- The first is a contact us page (name, email, notes)
  - When submitting, replace html with thank you page
- Thank you page, show name, email and notes
  - If data is missing, redirect back to contact us

---
#### @color[#e49436](Express) REST API

REpresentational State Transfer

HTTP verbs (GET/POST...) and URLs has meaning

Mainly being used for data tranfers (json)

Usualy /api/... (api/customers, api/customer/3)

---
#### @color[#e49436](Express) REST API

```js
app.get('/api/users', (req, res) => return all users);
app.get('/api/user:id', (req, res) => return user data);
app.post('/api/user', (req, res) => add new user);
app.delete('/api/user:id', (req, res) => delete from db);
```

---
#### @color[#e49436](Express) Structuring our app

We should create seperate modules for better structure the app

For instance, extract routes to their own module

How can we hook them into our app?

```js
module.exports = app => {
    app.get('/api/users', (req, res) => {...});
    app.post('/api/user', (req, res) => {...});
}
```

---
#### @color[#e49436](Express) Structuring our app

There's no right way of structuring our web app

There's always more than 1 solution which suits our needs

Keep app-logics seperated in simple yet reasonable way

---
#### @color[#e49436](Express) Express Generator

`> npm install express-generator -g`

`> express --view=ejs generated`

`> cd generated`

`> npm install`

`> npm start`

---
#### @color[#e49436](Express) Express Generator

Notice how routes are being used

```js
app.use('/', indexRouter);
app.use('/users', usersRouter);
```

users are being prefixed by */users*, and inside this router, we have normal routes

---
#### @color[#e49436](Node Part 2)

End Of Part 2


---?image=assets/images/grauman-at-experis.png



