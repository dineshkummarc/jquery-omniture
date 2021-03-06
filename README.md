# jQuery Omniture Plugin

Provides a convenient way for developers to add SiteCatalyst/Omniture tracking to pages and DOM elements.

## jQuery Omniture Plugin API

### omniture.view()

Provides the capability to apply pageview metrics to a particular route. This is a facade for <code>s.t()</code>.

* <code>{ String } route</code> - A human readable string representing the location you want tracked. This is a string but gets transformed into a regex.
* <code>{ Function } callback</code> - The callback you want executed that returns the metrics properties and sends them off to SiteCatalyst (Omniture).

### omniture.link()

Provides the capability to execute pseudo synchronous requests (img) to Omniture. This is a facade for <code>s.tl()</code>.

* <code>{ String | DOM Element } element</code> - The targeted node you want to listen to. eg/ $("button") or "#btn-register"
* <code>{ String } event</code> - The event you want to listen to on a particular node. eg/ "click", "hover", "mouseup", "keydown"
* <code>{ Function} callback</code> - The callback you want executed that returns the metrics properties and sends them off to SiteCatalyst (Omniture).

## Tutorial and Example Code

<pre>
  $(document).ready(function() {
      var config = {
        pageName: "DunderMifflin:Home"
      };

      var omniture = $(document).Omniture(config);

      //sinatra-style + express-style routing!
      
      omniture.view("index.html", function() {
        return { pageName: "DunderMifflin:Home", eVar1: "This is eVar1",eVar2: "This is eVar2" };
      });
      omniture.view("about", function() {
        return { pageName: "DunderMifflin:About", eVar1: "This is eVar1",eVar2: "This is eVar2" };
      });
      omniture.view("register", function() {
        return { pageName: "DunderMifflin:Register", eVar1: "This is eVar1",eVar2: "This is eVar2" };
      });

      omniture.link($("a"), "click", function(element) {
        return { event2: "login", prop3: element.attr('title'), eVar4: "evar4" };
      });
  });
</pre>
## MIT Licence

jQuery Omniture Plugin

Copyright (c) 2010 Jaime Bueza

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.