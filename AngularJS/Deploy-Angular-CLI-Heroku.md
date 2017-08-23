# Steps to Deploy Angular CLI App to Heroku

## Create account on heroku
create Heroku account, login and Click on `New`->`Create new app`
Name your app and choose the runtime.

## Creating server.js
In the root of your Angular app folder, create `server.js` file and add the following to it.

    const express = require('express');
    const app = express();
    const path = require('path');

    app.use(express.static(__dirname + '/dist'));

    app.listen(process.env.PORT || 8080);

    //Path Location Strategy

    app.get('/*', function(req, res) {
    res.sendFile(path.join(__dirname + '/dist/index.html'));
    })

    console.log('Console listening!');

## Install Express.js

Run `npm install express --save`


## Change settings in package.json

Move ` "@angular/cli": "1.3.1"` `"typescript": "~2.3.3"` and ` "@angular/compiler-cli": "^4.2.4"` from `"devDependencies"` to `"dependencies"`

Edit the `scripts` `  "start": "node server.js",` and add `"postinstall": "ng build --aot --target=production"` to scripts array.


## Deploying to heroku

**1.** Run `heroku login`. If you face login issues via git cmd then use windows/other cmd to login and then follow the next steps from git cmd.

**2.** `heroku git:remote -a heroku-project-name-here`

**3.** `$ git add .`

**4.** `git commit -m "initial heroku commit"`

**5.** `git push heroku master`

After the push is complete, it will show youthe link to your app.

You can also view the app link from HerokuDashboard
