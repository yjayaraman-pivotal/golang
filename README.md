# Hello
This is an sample app to show a web page with Hello world

## Background
When deploying Java applications, compilation of the application is down before doing a **cf push**. 
But in Go, since the code is compile to machine language on the target machine, compilation has to be done during staging. So the artifacts pushed during **cf push** are the source code and any dependencies.
In Go you use **Godep** to bundle dependencies. So you will need to install Godep after installing Go and you have to run **Godep save** before pushing an app.

Here the application starts a web server ands listens on a port for the requests. We have to make sure that the port is not hardcoded and uses the env variable set by CF.


## Running on [Pivotal Web Services][pws]

Log in.

```bash
cf login -a https://api.run.pivotal.io
```

Target your org / space. An empty space is recommended, to avoid naming collisions.

```bash
cf target -o myorg -s myspace
```

Set up dependencies.

```bash
godep save
```

Push the app. The manifest has the neccessary information to deploy the app.

```bash
cf push
```


[pws]:https://run.pivotal.io
