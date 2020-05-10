# DServers
Dart Server 
![](https://firebasestorage.googleapis.com/v0/b/dservers-5def7.appspot.com/o/Banner%20Image%2FDServers.png?alt=media&token=ca1c8b5a-e206-43b0-a85a-f6ed0ee28c6b)
##  Intro
This package will help you to start Dart servers easily.

## how to run dart code

[Official Dart Dev](https://dart.dev/tutorials/server/get-started)

## Example

[GitHub Repo Dservers Example ](https://github.com/rougerepublic23/DServer_examples)

## How to work
Initialise a main with Class 
```dart
void main() => MyApp();
```
now extend the DServer with you class
now you can acess DSerevers
```dart
class MyApp extends DServers {
  MyApp() {
   
   }
}

```
Now to start your server use start Server

```dart
startServer(
 ipAdress: InternetAddress.loopbackIPv4,
 port: 8000,
 onServerStart: (){},
 onurlNotFound:(){}
 parameters: []
 )

```
The StartServer can take a few parameters. They are ipaddress take the ipaddress of the server need to host, port is the needed port that need to show your server. 

### onServerStart

This will take a function which has parameters to set up the server. This server will call when the server starts. For example:
```dart
onServerStart: (server) {
          print(
              'ServerStart ${server.port} and ip adress ${InternetAddress.loopbackIPv4}');
        }
```
The onStart will get a function which have server as the parameter with server we can get things about our servers like server.port for getting in which server do our machine runs.

### onurlNotFound

This is function that dev can give if they need a custom 404 error page.
This function will trigger if there is a 404 error on the server request. For example:
```dart
 onurlNotFound: (request) {
          request.response
            ..write('Sorry This is 404 Error')
            ..close();
        }

```
onurlNotFound has a function as a parameter for request. We can get out the response when this function is called to users. Also we can set server status etc.To set server status you can add:
```dart
statusCode =HttpStatus.notFound
```
For example:
```dart
 onurlNotFound: (request) {
          request.response
          ..statusCode =HttpStatus.notFound
            ..write('Sorry This is 404 Error')
            ..close();
        }
```

### Parameters

It will take a list of parameters which takes in a parameters object.

```dart
parameters:[ 
  Parameters(),
  Parameters(),
]
```

#### Parameters object

The Parameters object takes parameters which is a string type representing the url
```dart
Parameters Parameters({String parameters, Function onRequest})
```
For example:
```dart
Parameters(
              parameters: '/',
              onRequest: (request) {
                request.response
                  ..write('Welcome to DServer')
                  ..close();
              })
```
### parameters url

The parameters will get a string which represent a string
```dart
String parameters
```

### onRequest
This will take a function which has a parameters request. This function will trigger when user acess those urls. For Example:
```dart
onRequest: (request) {
                request.response
                  ..write('Welcome to DServer')
                  ..close();
              }
```
the Request parameter can be used to do response whenever the function is called.
Users can also set server status by
```dart
statusCode =HttpStatus.<status>
```

In this you get which method is called on server by
```dart
request.method
```

Method can be any of GET, POST, UPDATE etc....

You can view HTML with this package or Dart language as a response. But I recommend you to use this as an api server to connect your Flutter web or app. Flutter provides much more in their Flutter Web and you can still write website in one code base instead of writing HTML.

## Future

This package was developed to show that Dart is not only a client side language but you can also use it serverside.
