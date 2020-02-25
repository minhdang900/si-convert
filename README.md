## Getting started

Run the following commands to get up and running.

```
git clone https://github.com/minhdang900/si-convert.git
cd si-convert
docker build -t si-convert .
docker run -d -p 3000:3000 si-convert
```

Open a browser window and go to http://localhost:3000/

## Calling it from Node

One way to consume the convert endpoint in Node.js code is by using the [request package](https://www.npmjs.com/package/request). 

```js
const fs = require('fs');
const request = require('request');

let req = request.post('http://localhost:3000/convert');
let form = req.form();
form.append('file', fs.createReadStream('video.mp4'));
form.append('format', 'gif');
req.pipe(fs.createWriteStream('image.gif'));
```
# Reference
File conversion can be a pain. Especially when you're trying to automate it. That's why I created Versed, a microservice specifically for that purpose.

Versed exposes a web API for converting files, and also comes with a simple web frontend for manual file conversion. 


It's currently powered by LibreOffice and FFmpeg, which means it supports the same file formats that those tools support, but you can easily add more tools to its arsenal.

Read the [blog post](http://aka.sb/Versed) to learn more!
