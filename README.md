
Reddpics is a commandline Subreddit image downloader, traversing subreddit pages, and downloading images (if any).  
Needs a valid API key and client id; see https://www.reddit.com/wiki/api how get both (don't worry, it's easy).  
Once you have those, create `~/.config/reddpics-login.sh`, with the following contents (you need to modify the values, obviously):

    export REDDPICS_APPID="<your-app-id>"
    export REDDPICS_APIKEY="<your-api-key>"
    export REDDPICS_USERNAME="<your-reddit-username>"
    export REDDPICS_PASSWORD="<your-reddit-password>"

Include this file in your `~/.bashrc` (or whichever shell you use), type `exec bash`, and you're pretty much good to go.  
If you're still not sure what to do, try 'reddpics --apihelp'.

----

# Features

  - Any URL whose Content-Type is that of an image (image/(jpeg|png|gif)), or webm (video/webm)
  - imgur pages (fairly complete)
  - gfycat links (fairly complete)
  - more to come, eventually

# Installation and Usage

Since reddpics uses some gems, you need to install them before you can use it:  

    gem install http redd trollop nokogiri colorize

After that, usage is as simple as it gets:

    # download the first 100 hot images from /r/aww to ./images/aww
    ./reddpics.rb aww --outputdir=./images/aww --limit=100 --maxpages=1 --section=hot

All supported options:

    -o, --outputdir=<s>    Output directory to download images to. default is './r_<subredditname>'.
                           You can use '%s' as template (for example, when downloading from several subreddits)
    -m, --maxpages=<i>     Maximum pages to fetch (note: values over 10 may not work!) (default: 10)
    -f, --filesize=<i>     Maximum filesize for images (default: 5000000)
    -l, --limit=<i>        How many links to fetch per page. Maximum value is 100 (default: 100)
    -s, --section=<s>      What to download. options are 'new', 'hot', 'top', and 'controversial'. (Default: top)
    -t, --time=<s>         From which timespan to download. options are 'day', 'week', 'month', 'year', and 'all'. (Default: all)
    -u, --username=<s>     Your reddit username - overrides 'REDDPICS_USERNAME'
    -p, --password=<s>     Your reddit password - overrides 'REDDPICS_PASSWORD'
    -a, --apikey=<s>       Your API key - overrides 'REDDPICS_APIKEY'
    -i, --appid=<s>        Your API appid - overrides 'REDDPICS_APPID'
    -#, --apihelp          Prints a quick'n'dirty explanation how to get your API credentials
    -h, --help             Show this message
