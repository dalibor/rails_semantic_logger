require 'rake/clean'
require 'rake/testtask'

$LOAD_PATH.unshift File.expand_path("../lib", __FILE__)
require 'rails_semantic_logger/version'

task :gem do
  system 'gem build rails_semantic_logger.gemspec'
end

task :publish => :gem do
  system "git tag -a v#{RailsSemanticLogger::VERSION} -m 'Tagging #{RailsSemanticLogger::VERSION}'"
  system 'git push --tags'
  system "gem push rails_semantic_logger-#{RailsSemanticLogger::VERSION}.gem"
  system "rm rails_semantic_logger-#{RailsSemanticLogger::VERSION}.gem"
end

Rake::TestTask.new(:test) do |t|
  t.pattern = 'test/**/*_test.rb'
  t.verbose = true
  t.warning = false
end

task default: :test
