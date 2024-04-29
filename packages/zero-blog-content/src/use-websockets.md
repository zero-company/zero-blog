# use-websockets

socket.io, websockets

https://github.com/vercel/swr/issues/41
https://stackoverflow.com/questions/10112178/differences-between-socket-io-and-websockets
https://swr.vercel.app/docs/subscription
https://www.fullstack.com/labs/resources/blog/develop-a-chat-application-using-react-express-and-socket-io
https://www.freecodecamp.org/news/simple-chat-application-in-node-js-using-express-mongoose-and-socket-io-ee62d94f5804/
https://www.reddit.com/r/node/comments/sa7wsw/how_to_scale_a_socketio_server_to_many_concurrent/
https://blog.logrocket.com/extend-express-request-object-typescript/
https://aaryanadil.com/pass-socket-io-to-express-routes-in-files/
https://codeburst.io/isomorphic-web-app-react-js-express-socket-io-e2f03a469cd3

<!-- prettier-ignore-start -->
app.all('*', (req, res, next) => {
  req.io = io
  let obj = {
    Host: req.headers.host,
    ContentType: req.headers['content-type'],
    Url: req.originalUrl,
    Method: req.method,
    Query: req.query,
    Body: req.body,
    Params: req.params,
  }
  console.log('Common Request is===========>', [obj])
  next()
})
<!-- prettier-ignore-end -->
