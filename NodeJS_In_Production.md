# Deploy a Node.js App for Production

## Create a Node.js Application

```
mkdir myapp && cd myapp

npm init

# We’ll use app.js as the entrypoint for our application
```

## Install Express

```
npm install express --save
```


vi app.js
```
const express = require('express')
const app = express()
const port = 8080

app.get('/', (req, res) => res.send('Hello World!'))
app.listen(port, () => console.log(`Example app listening on port ${port}!`))
```

## Checking the Endpoint

```
chmod +x ./app.js

node app.js
```

## Install PM2 ( process manager for Node.js applications )

```
sudo npm install -g pm2
```

## Manage Application with PM2

Execute the app.js’ application in the background 
```
pm2 start app.js
```

You can check for logs from PM2 by running:
```
pm2 logs
```

Applications that run under PM2 are automatically restarted when the application is killed or if it crashes


The subcommand ‘startup’ generates and configures a script specifically to launch PM2 and its managed process when the server boots.
```
pm2 startup systemd

systemctl status pm2-thomasmundt
```

## Set Up NGINX as a Reverse Proxy Server

vi /etc/nginx/sites-available/default
```
...
location / {
        proxy_pass http://localhost:8080;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

vi /etc/nginx/sites-available/default
```
location /app2 {
        proxy_pass http://localhost:8081;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
```


