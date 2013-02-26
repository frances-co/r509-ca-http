require 'rubygems'
require 'rspec/core/rake_task'
require "#{File.dirname(__FILE__)}/lib/r509/certificateauthority/http/version"

task :default => :spec
RSpec::Core::RakeTask.new(:spec) do
  ENV['RACK_ENV'] = 'test'
end

desc 'Run all rspec tests with rcov (1.8 only)'
RSpec::Core::RakeTask.new(:rcov) do |t|
  t.rcov_opts =  %q[--exclude "spec,gems"]
  t.rcov = true
end

namespace :gem do
  desc 'Build the gem'
  task :build do
    puts `yard`
    puts `gem build r509-ca-http.gemspec`
  end

  desc 'Install gem'
  task :install do
    puts `gem install r509-ca-http-#{R509::CertificateAuthority::HTTP::VERSION}.gem`
  end

  desc 'Uninstall gem'
  task :uninstall do
    puts `gem uninstall r509-ca-http`
  end
end

desc 'Build yard documentation'
task :yard do
  puts `yard`
  `open doc/index.html`
end
