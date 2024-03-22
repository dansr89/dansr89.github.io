source "https://rubygems.org"

# Hello! This is where you manage which Jekyll version is used to run.
# When you want to use a different version, change it below, save the
# file and run `bundle install`. Run Jekyll with `bundle exec`, like so:
#
#     bundle exec jekyll serve
#
# This will help ensure the proper Jekyll version is running.
# Happy Jekylling!
gem "jekyll", "4.3.3"
gem "html-proofer", ">= 3.10.0"
gem "webrick" # to fix 'cannot load rexml/parsers/baseparser'
gem "sprockets" #, "~> 3.7" # to fix rb_delegate wrong num of args
gem "json"

# This is the default theme for new Jekyll sites. You may change this to anything you like.
#gem "jekyll-swiss"

# If you want to use GitHub Pages, remove the "gem "jekyll"" above and
# uncomment the line below. To upgrade, run `bundle update github-pages`.
# gem "github-pages", group: :jekyll_plugins

# If you have any plugins, put them here!
group :jekyll_plugins do
   gem "jekyll-feed", "~> 0.6"
   gem "jekyll-sitemap"
   gem "jekyll-seo-tag"
   gem "jekyll-assets" #, "2.4.0"
   gem 'jekyll-bootstrap-sass' #, '~> 3.4.1'
end

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]