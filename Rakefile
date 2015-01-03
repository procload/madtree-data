require 'sinatra'
require 'data_mapper'
require 'open-uri'
require 'fog'
require 'untappd'
require 'json'

desc "This task is called by the Heroku scheduler add-on"
task :update_untappd do
  puts "Updating Untappd..."

  Untappd.configure do |config|
    config.client_id = '2977D98B3AA0DB9846E5D71F619E36A1E67D5F01'
    config.client_secret = '445B3550C7D39BE441A45B3FDFB2E4723F08FD52'
    config.gmt_offset = -5
  end

  brewery = Untappd::Brewery.info(16735)

  json = JSON.generate brewery.brewery

  File.open("views/untappd.json","w") do |f|
    f.write(json)
  end
  puts "done."
end


namespace :bundler do
  task :setup do
    require 'rubygems'
    require 'bundler/setup'
  end
end

task :environment, [:env] => 'bundler:setup' do |cmd, args|
  ENV["RACK_ENV"] = args[:env] || "development"
  require './app'
end

namespace :flatware do
  task :process => :environment do
    spreadsheet = Spreadsheet.all.each(&:write_content)
  end
end
