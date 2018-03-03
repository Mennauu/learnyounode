# learnyounode

Please note that I also used the official node documentation (as a source for all steps) which you can find here: [Node.js Documentation](https://nodejs.org/api/)


## Hello World

```javascript
console.log('Hello World')
```

## Baby Steps

```javascript
var sum = 0

for (i = 2; i < process.argv.length; i++) {
	sum += Number(process.argv[i])
}

console.log(sum)
```

## My First I/O!

```javascript
var fs = require('fs')
var buf = fs.readFileSync(process.argv[2])
var str = buf.toString().split('\n').length -1

console.log(str)
```

Used source: https://stackoverflow.com/questions/2850203/count-the-number-of-lines-in-a-java-string

## My First ASYNC I/O!

```javascript
var fs = require('fs')

fs.readFile(process.argv[2], 'utf8', function(err, fileContents) {
	if (err) {
		console.log(err)
	}
	var str = fileContents.split('\n').length -1
	console.log(str)
})
```

## Filtered LS

```javascript
var fs = require('fs')
var path = require('path')

fs.readdir(process.argv[2], function(err, dirContents) {
	if (err) {
		console.log(err)
	}
	for (i = 0; i < dirContents.length; i++) {
		if (path.extname(dirContents[i]) === '.' + process.argv[3]) {
			console.log(dirContents[i])
		}
	}
})
```

Used source: https://code-maven.com/list-content-of-directory-with-nodejs

## Make it Modular

program.js
```javascript
var module = require('./module')

var dir = process.argv[2]
var ext = process.argv[3]

module(dir, ext, function(err, dirContents) {
	if (err) return callback(err)

	dirContents.forEach(function(file) {
		console.log(file)
	})
}) 
```

module.js
```javascript
var fs = require('fs')
var path = require('path')

module.exports = function(dir, ext, callback) {

	fs.readdir(dir, function(err, dirContents) {
		if (err) return callback(err)

		dirContents = dirContents.filter(function(file) {
			return path.extname(file) === '.' + ext
		})

		callback(null, dirContents)
	})

}
```

## HTTP Client

```javascript
var http = require('http')

http.get(process.argv[2], function(response) {
    response.setEncoding('utf8')
    response.on('data', console.log)
    response.on('error', console.error)
}).on('error', console.error)
```

## HTTP Collect

```javascript
var http = require('http')
var bl = require('bl')

http.get(process.argv[2], function(response) {
    response.pipe(bl(function (err, data) {
      if (err) return callback(err)
      
      data = data.toString()
      console.log(data.length)
      console.log(data)
    }))
})
```

## Juggling ASYNC

## Time Server

## HTTP File Server

## HTTP Uppercaserer

## HTTP Json API Server
