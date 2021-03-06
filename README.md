gwtwwlinker
===========

HTML5 web worker for GWT with Elemental

About
----

This sample code shows how to compile GWT module to be used as HTML5 web worker.

`WorkerLinker` is the linker responsible for generating javascript code with minimal GWT overhead (like $wnd and $doc dependencies). Javascript template, located in series of print() commands, contains declaration of `$workergwtbridge` variable. It also registers message handler, which will pass data received from main process and pass it to `$workergwtbridge`.

`SampleWorker` is a class intended to run as worker, compiled with `WorkerLinker`. In `onModuleLoad` it instatiates `$workergwtbridge` function, which is now able to perform calculations implemented in GWT/Java and send back results.

`WebApp` is a simple GWT app which controls `SampleWorker` with Worker class from [GWT Elemental] package and shows data sent back from worker.

Remarks
----
* Sample gwt.xml's contains only Firefox permutation (`gecko1_8`), demo is compiled with this setting as well
* There is no automated permutation compilation/naming, you have to work it out yourself (feel free to send patch afterward)
* There is no automated permutation selection either
* The `$wnd = {JSON: JSON}; }` mock enables you to use autobeans, useful for pushing data structures between worker and main thread
* UserAgent and document compatMode checks are disabled for `SampleWorker`, as it wouln't work anyway (no access to neither GUI nor $doc)
* Sorry for plain Eclipse project, I'm not yet Maven-educated


Similar works
----
[speed tracer]  - contains breaky worker discussed [here]

[gwt-ns] - compatible with GWT 2.0, abandoned after GWT 2.2

Author
----
Tomasz Zieliński, tomasz.zielinski@gmail.com

License
----
Licensed under the Apache License, Version 2.0

Attribution
----
WorkerLinker class is directly derived from Titaniumj Mobile linker licensed under the Apache License, Version 2.0:
https://github.com/emitrom/titanium4j/blob/master/src/com/emitrom/ti4j/mobile/linker/TiMobileLinker.java

[GWT Elemental]: http://www.instantshift.com/2013/11/19/html5-features-with-gwt-elemental/
[gwt-ns]: http://code.google.com/p/gwt-ns
[Speed tracer]:https://developers.google.com/web-toolkit/speedtracer/
[here]:https://groups.google.com/forum/#!topic/google-web-toolkit/-vqHf5qMGgk