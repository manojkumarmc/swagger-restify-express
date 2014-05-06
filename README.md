CLKS Swagger
=========
<br>
CLKS Swagger is a layer which will enable easy documentation of REST layer
<br><br>

#### Make sure that your REST library is "restify"
```console
npm install restify
var restify =  require('restify')
```
<br><br>

#### Make sure that "swagger-ui" and "swagger-doc" is installed in your node.js server.
```console
npm install swagger-ui
npm install swagger-doc
```
<br><br>

#### Include clks-swagger where the REST paths are defined.
```console
cs = require('swagger-restify-express')
```
<br><br>

#### Have the restify server running
```console
var server = restify.createServer({
  name:"My REST server"
});

server.pre(restify.pre.userAgentConnection());
server.use(restify.bodyParser({ mapParams: false }));

server.get('/acs/:id', function(req, res) {
  res.send('hello from my REST server ' + req.params.name);
});

server.get('/acs/:id/getit/:here', function(req, res) {
  res.send('hello from my REST server ' + req.params.name);
});

server.post('/offload', streamOffloader.offload);

cs.init(server, {resourceName : 'swag'})

server.listen(3000, function() {
  console.log('%s listening at %s', server.name, server.url);
});
```
<br><br>
#### Make sure that you add the line, if you are using restify.
```console
cs.init(server, {resourceName : 'swag', // resource name
                 server: 'restify'})    // server library name
```

#### Make sure that you add the line, if you are using express.
```console
cs.init(app, {resourceName: 'token', // resource name
              server : 'express',    // server library name
	      staticResourceFolder: __dirname + '/node_modules/swagger-ui/dist'})
```

<br><br>  
#### Crank up your server
```sh
node app.js
```
<br><br>
#### Open up your browser
```sh
http://localhost:3000/index.html
```

<br><br>
#### In your resource entry edit box
```console
http://localhost:3000/swag
```

![alt tag](https://raw.githubusercontent.com/manojkumarmc/swagger-restify-express/master/swagger-ui.jpg)




 
  
   
   
  