require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name          = "thinner"
    gem.summary       = %Q{Thinner removes Varnish cache, as slowly as you need it to.}
    gem.description   = %Q{Thinner takes a list of urls or newline seperated stdin and purges them from Varnish.}
    gem.email         = "thejefflarson@gmail.com"
    gem.homepage      = "http://github.com/propublica/thinner"
    gem.authors       = ["Jeff Larson"]
    gem.executables   = "thinner"
    gem.require_paths = ['lib']
    gem.add_dependency "klarlack", "~> 0.0.6"
    gem.add_development_dependency "shoulda", ">= 0"
    # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: gem install jeweler"
end

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
end

begin
  require 'rcov/rcovtask'
  Rcov::RcovTask.new do |test|
    test.libs << 'test'
    test.pattern = 'test/**/test_*.rb'
    test.verbose = true
  end
rescue LoadError
  task :rcov do
    abort "RCov is not available. In order to run rcov, you must: sudo gem install spicycode-rcov"
  end
end

task :test => :check_dependencies

task :default => :test

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  version = File.exist?('VERSION') ? File.read('VERSION') : ""
  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "thinner #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end

desc "Render prose documentation"
task :gh do
  require 'erb'
  File.open("index.html", "w") do |f|
    f.write ERB.new(File.open("documentation/index.html.erb").read).result
  end
end

