### VSC Configuration to debug go app

1.- Install delve using from this [link
](https://github.com/derekparker/delve/tree/master/Documentation/installation).

2.- Click on Debug option.
![Debug VSC](https://image.ibb.co/jZM4vq/Screen-Shot-2018-10-26-at-16-40-41.png)

3.- Click here to create `.vscode/launch.json` file.
![Launch option](https://image.ibb.co/kEpeTA/Screen-Shot-2018-10-26-at-16-45-45.png)

4.- Replace default content with :

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Launch",
            "type": "go",
            "request": "launch",
            "mode": "debug",
            "remotePath": "",
            "port": 2345,
            "host": "127.0.0.1",
            "program": "${workspaceRoot}",
            "env": {},
            "args": []
        }
    ]
}
```

5.- Now set a break point anywhere

![Break point](https://image.ibb.co/g3R8bV/Screen-Shot-2018-10-29-at-08-27-15.png)

6.-