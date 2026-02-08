# === BUNDLER ===
# Bundler is a Ruby gem that installs gems in Gemfile and maintains their versions.
# Install it by
#   gem install bundler
# Run the following to initialize a new Bundler project in a new directory:
#   bundle init
# Add the required gems in Gemfile (e.g., "gem jekyll").
# Download and update the gems, ignoring Gemfile.lock:
#   bundle update
# To revert changes if the installation does not work,
#   replace the new Gemfile.lock with the original and run bundle install
# Download and update the gems according to Gemfile.lock:
#   bundle install
# This commands recommends the individual gems to update.
# === JEKYLL ===
# Jekyll is a Ruby gem, see:
#   https://jekyllrb.com/docs/ruby-101/
# To use it add "gem jekyll" to Gemfile.
# If deployment on GitHub is planned, add "gem github-pages" instead.
# Build the website in "_site" directory by
#   bundle exec jekyll build
# Build and serve the website by
#   bundle exec jekyll serve
# === GEMS ====
# Download the gems from:
source "https://rubygems.org"
# === GITHUB GEMS ===
# gem "jekyll", "~> 3.9.5"
gem "github-pages","~> 232", group: :jekyll_plugins
# Update github-pages often!:
#   bundle update github-pages
# Supported plugins and versions:
#   https://pages.github.com/versions/
group :jekyll_plugins do
  gem "jekyll-feed"
  gem 'jekyll-sass-converter'
  gem "jemoji" # Emojis supported by Git
  gem "rouge" # Syntax highlighter supported by GitHub Pages
end
# === LOCAL GEMS ===
# Gems installed only in local repository
install_if -> { ENV["GITHUB_ACTIONS"] != "true" } do
    puts "GitHub? #{ENV["GITHUB_ACTIONS"] == "true"}"
    gem "webrick", "~> 1.8"
end
