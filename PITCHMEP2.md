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
#### @color[#e49436](Express Generator)

- Express Generator

`> npm install -g express-generator`

Install dependencies

`> npm install`

---
#### @color[#e49436](Express Env Variables)

`> npm install dotenv --save`

Create .env file in root folder and inside:

```js
PORT=4100
```
And inside package.json:

```js
"start": "nodemon -r dotenv/config ./bin/www",
"startProd": "set PORT=3100 & nodemon -r dotenv/config ./bin/www"
```

---
#### @color[#e49436](Express Env Variables)

Run the server twice:

`> npm start`

`>npm run startProd`

And see the log

---
#### @color[#e49436](Express uuid)

We need to generate random GUID strings for our sessions

`npm install uuid --save`

```js
//Show it in homepage
router.get('/', function(req, res, next) {
  res.render('index', { title: 'Express', 
            sessionID: require('uuid/v4')() });
});

```

---
#### @color[#e49436](Express Session)

`> npm install express-session --save`

- Let's add our session middleware
  - Create middleware folder
- require express-session and uuid/4
- Use session({genid, secret, resave, saveUninitialized})
  - genid should return unique string,
  - secret is env key

---
#### @color[#e49436](Express Session)

```js
session({
    genid: req => {
        console.log(`session middleware. sessionID ${req.sessionID}`);
        return uuid();
    },
    secret: sessionSecret,
    resave: false, //For Store...later
    saveUninitialized: true //...later
})
```

---
#### @color[#e49436](Express Session)

Update .env, add

```js
SESSION_SECRET="My secret session key"
```

And use it for the session secret

---
#### @color[#e49436](Express Session)

express-session will add sessionID to the request

So let's try it out

```js
//Show it in homepage
router.get('/', function(req, res, next) {
  res.render('index', { title: 'Express', 
            sessionID: req.sessionID });
});

```

Watch the cookie in browser and in server console

Try refreshing, try to delete the cookie

---
#### @color[#e49436](Express Session)

Restart the server and go to homepage again

Again, watch the cookie in browser and in server console

What's wrong?

---
#### @color[#e49436](Express Session)

Sessions are stored in memory

If user sends hew session cookie, our middleware can't find it

So it initiates a new one...

We need to store our sessions to survive server restarts

---
#### @color[#e49436](Express Session Store)

`> npm install session-file-store --save`

Add it to our session config object (store property)

```js
const FileStore = require('session-file-store')(session);
//...
store: new FileStore(),
secret: sessionSecret,
///...

```

---
#### @color[#e49436](Express Session Store)

Try again with the browser and watch it restarts each time a request is coming

This is because session-store created a *sessions folder* and updates it

With the latest time the user reached the server

Help nodemon. Add in package.json

```js
nodemon --ignore sessions/
```

---
#### @color[#e49436](Express Session Store)

After a period when no interaction is made by the user

The session is ended and removed from store

```js
[session-file-store] Deleting expired sessions
[session-file-store] Deleting expired sessions
//...
```

---
#### @color[#e49436](Express Login)

Let's create a login route

- Create login router and hook it into express
- Add get and post routes
  - console log req.sessionID and req.body
  - render login ejs file with email and password

Run and verify post data is logged

---
#### @color[#e49436](Express Passport)

Install Passport as authentication middleware

`> npm install passport --save`

We'll be using *local* strategy (email+password)

`> npm install passport-local --save`

Or in one shot

`> npm install passport passport-local --save`

---
#### @color[#e49436](Express Passport)

- We will use Passport *authenticate('local')*
  - Which will use our auth method 
  - If authenticated, Passport will give us the req.*user* object

So first, implement authentication method

LocalStrategy assumes 'email' and 'password' are sent in the request's body

---
#### @color[#e49436](Express Passport)

Local Strategy authentication method

```js
passport.use(
 new LocalStrategy({ usernameField: 'email' },
  (email, password, done) => {
     console.log(`LocalStrategy ${email} ${password}`);
     const user = //... find the user by email
     if(!user) return done(null, false);
     if(user.password !== password) return done(null, false);
     return done(null, user);
  }
 )
);

```
---
#### @color[#e49436](Express Passport)

```js
passport.authenticate('local', (err, user, info) => {
  //login will be added if authentication succeeded
  req.login(user, err => {
      //req.user and req.session.passport are available
      next();
  });
})(req, res, next);
```

After successful authentication, 

Passport will establish a persistent login session

---
#### @color[#e49436](Express Passport) authenticate

- In our strategy, we use POST data to verify the user
- If verified, we get back to *authenticate()* 
  - And Passport added *req.login()* with the *user* as argument
    - We call login with the authenticated user
    - And eventually call the *next()* middleware

---
#### @color[#e49436](Express Passport) authenticate

- *req.login* then call *passport.serializeUser(user)*:
  - It saves user id to the session store
  - It adds user id as request.session.passport
  - It adds user object as request.user

```js
passport.serializeUser((user, done) => {
    done(null, user.id);
});
//{"cookie":{..."__lastAccess":...,"passport":{"user":101787}}

```

---
#### @color[#e49436](Express Passport) authenticate

```js
passport.deserializeUser((id, done) => {
    //Find the user... then
    if(user) done(null, user);
    else done(null, false);
});
```
- *passport.deserializeUser(userid)* will be called on next requests
- It'll match session id to the session store and retrieve user id
- Leaving us the opportunity to locate back the user data
- And add it back again to the request object

---
#### @color[#e49436](Express Passport) authorization

We can now protect some routes from being accessed

Using *req.isAuthenticated()*

Or creating custom middleware

```js
router.get('/users/:name', authorize, (req, res) => {
    //...got here if authorized
    //serve the page
});

```


```js

```

---
#### @color[#e49436](Express Session Store)
 
- Session Store


---
#### @color[#e49436](Express MySql)

- mysql
- students table
- REST

---
#### @color[#e49436](Express Auth)

- Passport

---
#### @color[#e49436](Node Part 2)

End Of Node Coure!

---?image=assets/images/grauman-at-wobi.png

