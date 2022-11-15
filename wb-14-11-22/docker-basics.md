# Tuesday 15th November 2022

**Today I Learned**
<br>

`Docker` can be used to run applications in isolated environments, with all dependencies included with the application. <br>

Docker uses the concept of images, which are snapshots of an environment that an application can run in, to instantiate containers for those applications to run in. <br> <br>
This is similar to the concept of virtual machines, however Docker containers share the host's OS, and only contain the code and dependencies neccessary for an application to run, rather than an entire OS. <br>
This makes them much faster to spin up. <br> <br>

We can create docker containers for applications by adding a single file to the app. A `Dockerfile`. <br><br>

----

<br>

Take this extremely basic Javascript application (app.js): <br>
```js
console.log("Hello, World!")
```
<br>
All we need to do to turn this app into a docker container is add a Dockerfile.

```docker
FROM node:ubuntu
COPY . /app
WORKDIR /app
CMD node app.js
```
<br>
This Dockerfile specifies that we want to... <br>
 
1) use a nodejs environment in ubuntu <br>
2) copy our app dir contents to /app dir in the container <br>
3) switch the working directory to /app <br>
4) run the command 'node app.js' to run the application <br>

<br>

To turn this application into a container image, we run a docker command: <br>
`docker build -t docker-test .` <br>
*build a docker image using the app and dockerfile in the current dir with the name 'docker-test'* <br><br>

A quick `docker image ls` should show that our image was created. <br>
```yml
REPOSITORY                 TAG       IMAGE ID       CREATED          SIZE
docker-test                latest    1c24f1998363   5 seconds ago    169MB
```
<br>

To run the container: `docker run docker-test` <br>

Which outputs
```yml
➜  hello-docker git:(master) ✗ docker run docker-test
Hello, World!
```

Yay!

<br><br>


## Ref. Links. Etc.
[DockerDocumentation](https://docs.docker.com/get-started/overview/) <br>
[TutorialVideo](https://www.youtube.com/watch?v=pTFZFxd4hOI) <br>
[DockerHub](https://hub.docker.com) <br>
