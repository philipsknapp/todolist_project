require 'rake/testtask'
require 'bundler/gem_tasks'
require 'find'

desc 'Say hello'
task :hello do
  puts "Hello there. This is the 'hello' task."
end

desc 'List visible files'
task :list do
  files = []
  Find.find(ENV["PWD"]) do |path|
    if FileTest.directory?(path)
      if File.basename(path).start_with?('.')
        Find.prune
      else
        next
      end
    else
      filename = path #path.gsub(/.*\//, '')
      files << filename unless File.basename(path).start_with?('.')
    end
  end
  puts files
end

desc 'Run tests'
task :default => :test 

Rake::TestTask.new(:test) do |t|
  t.libs << "test"
  t.libs << "lib"
  t.test_files = FileList['test/**/*_test.rb']
end