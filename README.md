# nodemon_test

Quick test to see whether inotify events work in containers with nodemon.

```
$ docker build . -t nodemon_test
$ docker run -it --rm -v `pwd`:/app nodemon_test
```

In another terminal:
```
$ touch index.js
```

Output on Docker for Mac:
```
> nodemon_test@1.0.0 start /app
> nodemon index.js

[nodemon] 1.12.1
[nodemon] to restart at any time, enter `rs`
[nodemon] watching: *.*
[nodemon] starting `node index.js`
hello world
[nodemon] restarting due to changes...
[nodemon] starting `node index.js`
hello world
```

So, it does work in this case. However, if you're running Docker in a virtual machine or over a network share, the inotify events not make it as far as docker.
