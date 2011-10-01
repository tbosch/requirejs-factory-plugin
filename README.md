Require.js Factory Plugin
===============

Description
------------
This is a requirejs plugin that allows to inject the factory of modules into otehr modules.
This is most useful for unit-tests, so that they are able to instantiate the module that should be tests with mocked dependencies
as often as needed.

This is especially useful if your modules are stateful, and the tests change the state of the modules.

Requirejs does not yet provide this feature, see the group discussion here:
[http://groups.google.com/group/requirejs/browse_thread/thread/e6964d924687bd77](http://groups.google.com/group/requirejs/browse_thread/thread/e6964d924687bd77)


Usage
-------------

Define the modules that as normal, e.g.
    
    define('mymodule', ['dep1'], function(dep1) {
    ...
    });

The factory of this module is the function

    function(dep1) {
    ...
    };


In your unit-test you can then inject that factory function with the following syntax:

    define('mytest', ['factory!mymodule'], function(myModuleFactory) {
    ...
    }
    
Notes
-------------
This uses an internal callback `require.execCb` of requirejs to get a hold of the module factories.
This callback is also used by the requirejs optimizer `r.js`, however, this might break in a future requirejs version.
Be sure to load this plugin as soon as possible, so it can catch all needed factory functions
e.g. with `require(['factory!', 'unittest1', ...])`.


During optimization, this will create named modules that contain the factory function. 
By this, this module is no more used after optimization.
In the example above,
this will dynamically create the following module:

    define('factory!mymodule', function() {
        return function(dep1) {
            ...
        }    
    }


