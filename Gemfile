source "http://rubygems.org"

require 'json'
require 'open-uri'
versions = JSON.parse(open('https://pages.github.com/versions.json').read)

gem "jekyll", "~> 3.4.2"
gem "jekyll-sitemap"
gem "jekyll-gist"
gem "jekyll-feed"
gem 'github-pages', versions['github-pages']
