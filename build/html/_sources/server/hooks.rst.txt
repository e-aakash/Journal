Hooks
=====

What are hooks?
---------------
Todo

Where do we keep them?
----------------------
The hook.rb script resides in ``/var/www/``. The configurations for hooks can be found in the Github Repository's settings page under the Webhooks tab from the left panel.

.. code-block:: ruby

    # hook.rb
    require 'sinatra'
    require 'json'
    require 'rubygems'

    set :bind, '0.0.0.0'

    post "/payload" do
    request.body.rewind  # in case someone already read it
    data = JSON.parse request.body.read
    #"Hello #{data['repository']['html_url']}!"
    journal = "https://github.com/TheFlash98/Journal"
    website = "https://github.com/nihal111/WnCC"
    if journal == "#{data['repository']['html_url']}"
        output = `cd /var/www/journal.wncc-iitb.org; git pull;`
    #`svn checkout https://github.com/TheFlash98/Journal/trunk/build/html; cp .htaccess html/`
        p output
    end
    if website == "#{data['repository']['html_url']}"
        output = `cd /var/www/wncc-iitb.org; mv html _site; git pull origin production; mv _site html`
    #`svn checkout https://github.com/nihal111/WnCC/trunk/_site; rsync -av _site/ html/; `
        p output
    end
    end


Hooks we have
-------------
The hooks we have currently are-

1. Main Website
2. Journal

How to run?
-----------

**Test Run** --- It is recommended to do a test run before you set up the hook to run forever in the background.

**Background Process** --- To fork and create a background process that logs all output in a desired file, use this-

``sudo nohup sudo ruby hook.rb -o 0.0.0.0 -p 1981 >>/home/nihal/hooklog.txt &``

**Explanation**-
nohup-
port-
log-
forking-

Logging
-------
The logs are all saved to the file- 