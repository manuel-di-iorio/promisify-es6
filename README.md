# Promisify-es6
Promisify callback-style functions to ES6 promises

###Install it with:
  
    npm i --save promisify-es6
    or
    git clone https://github.com/manuel-di-iorio/promisify-es6.git
    
###Example:

    var promisify = require("promisify-es6");
    var fs = require("fs");
    var readFile = promisify(fs.readFile);
    
    readFile("test.js")
     .then(function(content) {
        console.log(content.toString());
     })
     .catch(function(err) {
        console.error(err);
     });
    
A promisifed function is still callable with the callback style:

    readFile("test.js", function(err, content) { //etc...
    
You can even promisify entire modules or arrays:

    var readFile = promisify(require("fs")).readFile;
    
## API

    promisify(method, options)
    
    *Method* can be a function or an array/map of functions to promisify
    
    *Options* can have the following properties:
    
        `context`: The context which to apply the called function (by default is the function itself)
        `replace`: When an array/map is passed and this is truthy, it will replace the original object 
    
###Test with:

    npm test
