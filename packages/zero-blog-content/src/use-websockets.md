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
https://nexocode.com/blog/posts/websockets-friend-or-foe/
https://www.reddit.com/r/AskProgramming/comments/11szztb/why_is_it_that_websockets_havent_seen_much/
https://medium.com/@selieshjksofficial/crafting-reliable-socket-io-code-e062405c7741
https://stackoverflow.com/questions/25023118/is-socket-io-a-reliable-chat-server-for-large-number-of-users-if-yes-whats-you
https://socket.io/docs/v4/delivery-guarantees

https://www.google.com/search?client=firefox-b-d&q=socket.io+react+context
https://dev.to/bravemaster619/how-to-use-socket-io-client-correctly-in-react-app-o65
https://github.com/pmndrs/zustand/discussions/1651
https://stackoverflow.com/questions/51372997/socket-io-how-to-send-multiple-messages-sequentially

why even implement websocket if it's too unreliable and you'll end up polling anyway
Long polling (client pull)
Short polling (client pull)
Server-Sent Events (server push)
Real-time database from Firebase (with WebSockets under the hood)

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
