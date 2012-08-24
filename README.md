Require.js Factory Plugin (Overcome by another project)
===============

This plugin does no more work with the current requirejs version.
Please see the isolate plugin: [https://github.com/tnwinc/Isolate](https://github.com/tnwinc/Isolate).

Description
------------
This is a requirejs plugin that allows to inject the factory of modules into otehr modules.
This is most useful for unit-tests, so that they are able to instantiate the module that should be tests with mocked dependencies
as often as needed.

This is especially useful if your modules are stateful, and the tests change the state of the modules.

Requirejs does not yet provide this feature, see the group discussion here:
[http://groups.google.com/group/requirejs/browse_thread/thread/e6964d924687bd77](http://groups.google.com/group/requirejs/browse_thread/thread/e6964d924687bd77)


