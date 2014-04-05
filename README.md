#AngularSocket

A quick and dirty websocket wrapper for angular.  It gives some convenience methods for communicating with websockets from different services or controllers so that you can worry more about your implementation and less about how angular deals with sockets.

##Methods

##`.get(name, url)`

This method returns a wrapped websocket that will work without a call to $scope.$apply. 

The `name` that is passed to the factory can be used at any point during the lifecycle of your application to retrieve the same socket instance, and thus does not need to constantly disconnect and reconnect with the server. The `url` is simply the endpoint url of your websocket server-side application.

The socket instance returned will have two methods: `emit(name, data)` and `on(event, handler)`.

###`emit(name, data)`

`emit` passes a named event to the server. This is similar to the socket.io functionality, but returns a promise will be fulfilled on confirmation or response from the server.

###`on(event, handler)`

`on` accepts an event name and a handler function that will be invoked when that named event is thrown by the server in the format `{event: <eventName>, data: { /*...data...*/ }}`. The handler will be passed any data sent by the server.

