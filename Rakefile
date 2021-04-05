require 'bundler'
Bundler.setup

namespace :docker do
  desc "build docker images"
  task :build => ['translations:build'] do
    puts "Building globalbitcoincash docker image"
    puts `docker build -t globalbitcoincash .`
  end
end

namespace :translations do
  require 'erb'
  require 'fileutils'
  require 'i18n'
  require "i18n/backend/fallbacks"
  I18n::Backend::Simple.send(:include, I18n::Backend::Fallbacks)
  I18n.load_path = Dir['./translations/*.yml']
  I18n.default_locale = :en

  desc "build translated html files"
  task :build do
    puts "Building globalbitcoincash translated html files"
    nginx_template = File.read('nginx.conf.erb')
    nginx_renderer = ERB.new(nginx_template)
    File.write(File.join('.', 'nginx.conf'), nginx_renderer.result())
    template = File.read('index.html.erb')
    renderer = ERB.new(template, nil, '-')
    I18n.available_locales.sort.each do |locale|
      puts "Building #{locale}"
      I18n.locale = locale
      File.write(File.join('.', 'html', "index.#{locale}.html"), renderer.result())
      File.write(File.join('.', 'html', 'index.html'), renderer.result()) if locale == :en
      File.write(File.join('.', 'html', locale.to_s.downcase, 'index.html'), renderer.result())
    end
  end
end

task :default => 'docker:build'
