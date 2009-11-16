require 'rubygems'
require 'rake'
require 'rake/clean'
require 'rake/testtask'
require 'rake/packagetask'
require 'rake/gempackagetask'
require 'rake/contrib/rubyforgepublisher'
require 'fileutils'
include FileUtils

# impart all tasks in lib/tasks/
Dir['lib/tasks/*.rake'].each { |task| import task }

task :default => :test

desc "Run unit tests"
Rake::TestTask.new(:test) do |test|
  test.libs << "test"
  test.pattern = "test/ts_all.rb"
  test.verbose = true
end

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "rets4r"
    gem.summary  = 'A native Ruby implementation of RETS (Real Estate Transaction Standard).'
    gem.authors   = ['Scott Patterson', 'John Wulff', 'bgetting']
    gem.email    = ['scott.patterson@digitalaun.com', 'john@johnwulff.com', 'brian@terra-firma-design.com']
    gem.homepage = 'http://rets4r.rubyforge.org/'
    gem.files =  FileList["[A-Z]*", "{examples,lib,test}/**/*"]
    gem.rubyforge_project = 'rets4r'
    gem.extra_rdoc_files = ['CONTRIBUTORS', 'README', 'LICENSE', 'RUBYS', 'GPL',
      'CHANGELOG', 'TODO' ]
    gem.rdoc_options << '--main' << 'README'
    gem.test_files = 'test/ts_all.rb'
    # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
  end

rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: sudo gem install jeweler"
end

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  if File.exist?('VERSION.yml')
    config = YAML.load(File.read('VERSION.yml'))
    version = "#{config[:major]}.#{config[:minor]}.#{config[:patch]}"
  else
    version = ""
  end

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "rets4r #{version}"
  rdoc.options << '--line-numbers' << '--inline-source'
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end
