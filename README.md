# learnyounode

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
		if (path.extname(dirContents[i]) === '.' + process.argv[3]) 
			console.log(dirContents[i])
	}
})
```

Gebruikte bronnen: https://code-maven.com/list-content-of-directory-with-nodejs

## Make it Modular

## HTTP Client

## HTTP Collect

## Juggling ASYNC

## Time Server

## HTTP File Server

## HTTP Uppercaserer

## HTTP Json API Server
