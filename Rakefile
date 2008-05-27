require 'rubygems'
require 'rake/gempackagetask'
require 'merb-core/tasks/merb_rake_helper'

NAME = "merb-gen"
GEM_VERSION = Merb::MORE_VERSION rescue "0.9.4"
AUTHOR = "Yehuda Katz"
EMAIL = "wycats@gmail.com"
HOMEPAGE = "http://www.merbivore.com"
SUMMARY = "Merb More: Merb's Application and Plugin Generators"

spec = Gem::Specification.new do |s|
  s.rubyforge_project = 'merb'
  s.name = NAME
  s.version = GEM_VERSION
  s.platform = Gem::Platform::RUBY
  s.has_rdoc = true
  s.extra_rdoc_files = ["README", "LICENSE", 'TODO']
  s.summary = SUMMARY
  s.description = s.summary
  s.author = AUTHOR
  s.email = EMAIL
  s.homepage = HOMEPAGE
  s.bindir = "bin"
  s.executables = %w( merb-gen )

  # Uncomment this to add a dependency
  s.add_dependency "merb-core", ">= 0.9.4"
  s.add_dependency "rubigen", ">= 1.2.4"

  s.require_path = 'lib'
  s.files = %w(LICENSE README Rakefile TODO) +
          Dir.glob("{lib,bin,spec,app_generators,merb_default_generators,merb_generators,rspec_generators,test_unit_generators}/**/*")
end

Rake::GemPackageTask.new(spec) do |pkg|
  pkg.gem_spec = spec
end

task :install => [:package] do
  sh %{#{sudo} gem install #{install_home} pkg/#{NAME}-#{GEM_VERSION} --no-update-sources}
end

namespace :jruby do
  task :install do
    sh %{#{sudo} jruby -S gem install #{install_home} pkg/#{NAME}-#{GEM_VERSION}.gem --no-rdoc --no-ri}
  end
end


