# nodejs-develope

### Install
- Installing all.
```
    npm install
```
#### FS and Command Line Args
- Getting input from users
```
    console.log(process.argv)
```
Terminal
```
    node app.js Tram 
    // Because of console.log, it shows 
    [
        '/opt/homebrew/Cellar/node/17.7.1/bin/node',
        '/Users/tramtran/Desktop/nodejs-developer/app.js',
        'Tram'
    ]
```
Notes: it can not take your words as you want, so we use "Yargs" npm.
- Install "Yargs" npm ``` npm install yargs ```

#### Store DATA with JSON
Convert JS Object to JSON string
```
    const book = {
    title: "ABC",
    author: "Alex"
    }
    const bookJson = JSON.stringify(book)
```
Convert JSON files to JS Object
```
    const fs = require("fs");
    
    const bookBuffer = fs.readFileSync("book.json")
    const bookJSON = bookBuffer.toString()
    const book1 = JSON.parse(bookJSON)

    // change title of book
    book1.title = "Red Bear"

    const book1Json = JSON.stringify(book1)
    fs.writeFileSync("book.json", book1Json)
```

#### Debugging Nodejs
```
    console.log()
    //or
    debugger
```
#### Weather App
- Heroku Deploy: [Weather Demo](https://tram-weather-app.herokuapp.com/).
- Dark Sky API or WeatherStack, sign up an account.

- Install `postman-request` npm
```
    npm install postman-request
```
In Weather App
```
    request(url, (error, response, body) => {
        // parse data JSON string to JS Obj
        const data = JSON.parse(response.body)
        console.log(data.current)
    });
// OR
    request({url, json: true }, (error, response, body) => {
        console.log(response.body.current)
    });
```

- Install `dotenv` npm
```
    npm install dotenv
```

- Using `MapBox` to search geocoding details latitude and longtitude at a certain place 

#### Server
- Customizing Views Directory
Before
```
    const express = require("express");
    const app = express();

    // set up, pointing to file with extension "hbs"
    app.set("view engine", "hbs");
```
Then
```
    const express = require("express");
    const path = require("path");

    const app = express();
    const viewPath = path.join(__dirname, "../templates/views");

    // set up, pointing to file with extension "hbs"
    app.set("view engine", "hbs");
    // customizing views directory
    app.set("views", viewPath);
```
