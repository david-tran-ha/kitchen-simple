gem 'rubocop', '>=0.33.0'

require 'foodcritic'
require 'rspec/core/rake_task'
require 'rubocop/rake_task'

desc 'Run tests'
task :default => [:test1, :test2]

desc 'This is Test 1. Will print Test 1'
task :test1 do
	ruby 'test.rb'
end


desc 'This is Test 2. Will print Test 2'
task :test2 do
	puts 'This is test 2'
	puts 'This is the PATH environment: ' + ENV['PATH'] 
end

# Style tests. Rubocop and Foodcritic
namespace :style do
  desc 'Run Ruby style checks'
  RuboCop::RakeTask.new(:ruby)

  desc 'Run Chef style checks'
  FoodCritic::Rake::LintTask.new(:chef) do |t|
    t.options = {
      fail_tags: ['any'],
      tags: ['~FC005', '~FC003', '~FC058'],
	  cookbook_paths: [ '/Users/duc/Software/ChefTest/chef-repo/cookbooks/sumologic-collector-chef-cookbook', '.' ]
    }
  end
end

desc 'Run all style checks'
task style: ['style:chef', 'style:ruby']
