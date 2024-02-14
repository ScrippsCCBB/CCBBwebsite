How to run this website locally:



Open Git Bash.

Navigate to the publishing source for your site. For more information, see "Configuring a publishing source for your GitHub Pages site."

Run bundle install.

Run your Jekyll site locally.

$ bundle exec jekyll serve

> Configuration file: /Users/octocat/my-site/_config.yml

>Source: /Users/octocat/my-site

>   Destination: /Users/octocat/my-site/_site

> Incremental build: disabled. Enable with --incremental

>  Generating...

>   done in 0.309 seconds.

> Auto-regeneration: enabled for '/Users/octocat/my-site'

> Configuration file: /Users/octocat/my-site/_config.yml

> Server address: http://127.0.0.1:4000/

>   Server running... press ctrl-c to stop.

Note: If you've installed Ruby 3.0 or later (which you may have if you installed the default version via Homebrew), you might get an error at this step. That's because these versions of Ruby no longer come with webrick installed.

To fix the error, try running bundle add webrick, then re-running bundle exec jekyll serve.


To preview your site, in your web browser, navigate to http://localhost:4000.
