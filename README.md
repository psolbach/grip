spark.js
=======

Spark.js is a lightweight (1kb) dependency insertion switch for Javascript modules.  
Borrowing from require.js, a single script tag in your HTML will

1. Insert an array of unpacked Javascript modules for development.
2. Or a pretailored minified script without overhead.

## Usage

Options live inside the 'module.js' which is referenced via a data-tag in the `<script>`.  
A sample embed would be:

    <script charset="utf-8" data-options="/dpatools/static/dist/modules.js"
    src="/dpatools/static/vendor/spark.js"></script>
    
Your `module.js` should look something like this:

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
    
## Workflow with shell.js

Using a shell script in the flavor of https://github.com/arturadib/shelljs one could go about and
fully integrate the generation of `modules.js` into the make/debug process.

    function makeSpark(d,b,p,m) {
      var o = { "debug": d, "baseUrl": b, "min": "/" + p,
        "modules": d ? m : [] }, file = "'use strict'; window.opt = "
         + JSON.stringify(o)
      
      file.to(conf.base + conf.modules);
    }
    
## Questions?

Feel free to drop a line to p@psolbach.com or @_p0wly
