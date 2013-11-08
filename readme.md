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
            </s

                $('[data-gadget]').each(function(_, elem) {
                  root.declareIframedGadget($(elem).attr('data-gadget'), $(elem)).done(function(gadget) {
                    gadget.getInterfaceList().done(function(list) {
                        if (list.indexOf('http://www.renderjs.org/interface/blob-editor') > -1) {
                            gadget.setContent($(elem).attr('data-gadget-content'));
                        } else if (list.indexOf('http://www.renderjs.org/interface/text-editor') > -1) {
                            $.ajax($(elem).attr('data-gadget-content')).done(function(resp) {
                                gadget.setContent(resp);
                            });
                        } else {
                            console.log('gadget does not implement any standard form');
                        }
                    });
                  });
                });
              });
            })(jQuery, rJS, window);
            </script>
          </head>
          <body>
            <div id="webviewer"></div>
          </body>
        </html>


        ;(function($, rJS, window) {
          rJS(window).ready(function() {
            var root = rJS(this);
            $('[data-gadget]').each(function(_, elem) {
              root.declareIframedGadget($(elem).attr('data-gadget'), $(elem)).done(function(gadget) {
                gadget.getInterfaceList().done(function(list) {
                    if (list.indexOf('http://www.renderjs.org/interface/blob-editor') > -1) {
                        gadget.setContent($(elem).attr('data-gadget-content'));
                    } else if (list.indexOf('http://www.renderjs.org/interface/text-editor') > -1) {
                        $.ajax($(elem).attr('data-gadget-content')).done(function(resp) {
                            gadget.setContent(resp);
                        });
                    } else {
                        console.log('gadget does not implement any standard form');
                    }
                });
              });
            });
          });
        })(jQuery, rJS, window);
