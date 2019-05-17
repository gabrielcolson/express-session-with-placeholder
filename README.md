# express-session-with-placeholder

Simple fork of [express-session](https://github.com/express/session) which adds
a placeholder in the cookie in order to store additional information you do
not want to store server-side.

## Installation

This is a [Node.js](https://nodejs.org/en/) module available through the
[npm registry](https://www.npmjs.com/). Installation is done using the
[`npm install` command](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```sh
$ npm install express-session-with-placeholder
```

## Usage

You can use this package as the real express-session.
To use the placeholder just store your data in ``req.placeholder``.
```js
app.post('/sign-in', (req, res) => {
  // ...

  req.placeholder = 'foo';
  res.end();
});
```

Your placeholder is now stored in ``req.placeholder`` if the cookie
is correctly set.
```js
app.get('/bar', (req, res) => {
  if (res.placeholder !== 'foo') {
    return res.status(403).end();
  }
  return res.end('bar');
});
```

## License

[MIT](LICENSE)
