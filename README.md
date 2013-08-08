## Heroku compatible node.js websockets example

Install dependencies locally

```
$ npm install
```

Create Heroku app

```
$ heroku create -a node-ws-example
Creating node-ws-example... done, region is us
http://node-ws-example.herokuapp.com/ | git@heroku.com:node-ws-example.git
Git remote heroku added
```

Enable websockets labs feature

```
$ heroku labs:enable websockets
Enabling websockets for node-ws-example... done
WARNING: This feature is experimental and may change or be removed without notice.
For more information see: Enable websocket support
```

Push app to Heroku

```
$ git push heroku master
Counting objects: 7, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (5/5), done.
Writing objects: 100% (7/7), 911 bytes, done.
Total 7 (delta 0), reused 0 (delta 0)

-----> Node.js app detected
...
-----> Launching... done, v4
       http://node-ws-example.herokuapp.com deployed to Heroku

To git@heroku.com:node-ws-example.git
 * [new branch]      master -> master
```

Run client locally

```
$ SERVER=node-ws-example.herokuapp.com node client.js 
received: server says HELLO via websockets!
^C
```

Check logs for server console output

```
$ heroku logs
...
2013-08-08T22:25:11.200510+00:00 heroku[web.1]: Starting process with command `node server.js`
2013-08-08T22:25:13.198430+00:00 heroku[web.1]: State changed from starting to up
2013-08-08T22:25:50.994732+00:00 app[web.1]: received: client sends something via websockets
2013-08-08T22:25:54.784814+00:00 heroku[router]: at=info method=GET path=/path host=node-ws-example.herokuapp.com fwd="69.181.105.52" dyno=web.1 connect=5ms service=3902ms status=101 bytes=14
```
