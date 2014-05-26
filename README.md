grip.js
=======  

![asd](http://heimdash.com/grip.svg)  
  
Grip.js is a lightweight (1kb) insertion switch for Javascript modules.  
Borrowing from require.js, a single script tag in your HTML will

1. Insert an array of unpacked Javascript modules for development.
2. Or a pretailored minified script without overhead.

### Usage

Options live inside a `.js` which is referenced via data-tag in the `<script>`.  
A sample embed would thusly look a whole lot like this:

    <script charset="utf-8" data-options="/static/dist/modules.js"
    src="/vendor/grip.min.js"></script>
    
Your `modules.js` should look something like this:

    'use strict';
    window.opt = {
    	"debug": true,
    	"baseUrl": "optional/static/root",
    	"min": "/path/to/your.min.js",
    	"modules": [
    		"your",
    		"modules"
    		]
    }
    
### Workflow with shell.js

Using a shell script in the flavor of [shelljs](https://github.com/arturadib/shelljs) one could go about and
fully integrate the generation of `modules.js` into the make/debug process.
Consider this snippet where d, b, p, m map to opt.debug, opt.baseUrl, opt.min, opt.modules.

    function makeSpark(d,b,p,m) {
      var o = { "debug": d, "baseUrl": b, "min": "/" + p,
        "modules": d ? m : [] }, file = "'use strict'; window.opt = "
         + JSON.stringify(o)
      
      file.to(conf.base + conf.modules);
    }


    
### Questions?

Feel free to drop a line to p@psolbach.com or @_p0wly

### Acknowledgements

Aerosmith didn't sue. Yet.
