grip.js
=======
<a href="https://codeclimate.com/github/p0wly/gripjs"><img src="https://codeclimate.com/github/p0wly/gripjs.png" /></a>

![asd](http://heimdash.com/grips.svg)  
  
  
  
Grip.js is a lightweight (1kb) insertion switch for Javascript files.  
This can help replace Grunt or any other full-fledged build system in favor  
of a more minimal approach. Borrowing from [require.js](https://github.com/jrburke/requirejs),  
a single script tag in your HTML will

1. Insert an array of unpacked Javascript modules for development.
2. Or a pretailored & minified production version of your JS.

### Performance

Your HTML remains untouched. Scripts are pulled in a dynamic fashion.  
Field tests have proven that this can speed up perceived and actual load time  
-- so don't wander off just yet.

### Usage

Options live inside a `.js` which is referenced via data-attribute in the `<script>`.  
A sample embed would thusly look a whole lot like this:

    <script charset="utf-8" data-options="modules.js" src="grip.min.js"></script>
    
Your `modules.js` should resemble something like this:

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

    function makeGrip(d,b,p,m) {
      var o = { "debug": d, "baseUrl": b, "min": "/" + p,
        "modules": d ? m : [] }, file = "'use strict'; window.opt = "
         + JSON.stringify(o)
      
      file.to(conf.base + conf.modules);
    }


    
### Questions?

Feel free to drop a line to p@psolbach.com or @p0wly

### Acknowledgements

Aerosmith didn't sue. Yet.
