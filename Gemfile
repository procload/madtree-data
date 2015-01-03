source 'https://rubygems.org'

gem 'nokogiri', '~> 1.5.11'
gem 'sinatra'
gem 'sinatra-jsonp'
gem 'rack-cors', :require => 'rack/cors'
gem 'data_mapper'
gem 'fog'

gem "untappd"

group :production do
  gem 'pg'
  gem 'dm-postgres-adapter'
end

group :development do
  gem 'dm-sqlite-adapter'
end
