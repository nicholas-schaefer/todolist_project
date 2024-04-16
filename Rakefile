require "rake/testtask"
require 'find'
require "bundler/gem_tasks"

desc 'Say hello'
task :hello do
  puts "Hello there. This is the 'hello' task."
end

desc 'Run tests'
task :default => :test

Rake::TestTask.new(:test) do |t|
  t.libs << "test"
  t.libs << "lib"
  t.test_files = FileList['test/**/*_test.rb']
end




desc 'Calculate size'
task :size do
  total_size = 0
  files =  FileList['lib/*']

  files.each do |path|
    if FileTest.directory?(path)
      if File.basename(path).start_with?('.')
        Find.prune       # Don't look any further into this directory.
      else
        next
      end
    else
      total_size += FileTest.size(path)
    end
  end
  puts total_size
end
