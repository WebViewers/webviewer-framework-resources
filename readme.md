# WebViewer Framework Resources

These are resources which are needed in order to integrate WebViewers
into your web application framework. How exactly WebViewers are implemented
is largely an implementation detail and you can find more information here
http://webviewers.org/xwiki/bin/view/Main/WebApplicationTutorial
but these files are necessary in order to instanciate a WebViewer.

## Example of WebViewer Instanciation

This example makes use of the `textedit-webviewer` which is available in the
webviewers github repostitory.

        <html>
          <head>
            <script src="renderjs_jquery.js"></script>
            <script src="jschannel.js"></script>
            <script src="renderjs.js"></script>
            <script>
              rJS(window).ready(function() {
                var root = rJS(this);
                var elem = document.getElementById('webviewer');
                root.declareIframedGadget("path/to/webviewer/index.html", elem).done(function (gadget) {
                    gadget.setContent("hello world!");
                });
              });
            </script>
          </head>
          <body>
            <div id="webviewer"></div>
          </body>
        </html>
