require 'colored'
require 'rspec/core/rake_task'

task :default => [:print_help]

task :print_help do
  puts "\nPlease specify a task to run. To list all available tasks, run 'rake -T' or 'rake --tasks'.\n\n"
end

desc 'Run a full clean build and full tests'
task :build => [:clean, :compile, :test]

desc 'Run all tests and static analysis'
task :test => [:static_analysis, :unit_test, :integration_test]

desc 'Clean workspace and logs'
task :clean do
  print_header("Running task: clean")
  puts "Cleaning your workspace..."
  if FileTest.exists?('rspec.log')
    puts "Removed rspec.log"
    `rm rspec.log`
  end
  if FileTest.exists?('demo.war')
    puts "Removed previous build: demo.war..."
    `rm demo.war`
  end
  if FileTest.exists?('coverage/rcov/index.html')
    puts "Removed coverage dir..."
    `rm coverage/rcov/index.html`
  end

  print_success("Your workspace is clean")
end

desc 'Compile your source code'
task :compile do
  print_header("Running task: compile")
  puts "Compiling source code"

  1.upto(10) do |n|
    print "."
    sleep 1 # second
  end
  puts "\n\n"
  `touch demo.war`
  print_success "\nGenerated demo.war"
end

desc 'Run all static analysis'
task :static_analysis do
  print_header("Running task: static_analysis")
  sh "/usr/local/bin/tailor -c ./.tailor"
end

desc 'Run unit tests'
task :unit_test do
  print_header("Running task: unit_test")
 # sh '/usr/local/bin/rspec -c spec/unit/*_spec.rb --deprecation-out rspec.log --format documentation'
end

desc 'Run all integration tests'
task :integration_test do
  print_header("Running task: integration_test")
  print_warning("No integration tests found in test/integ. Please add them.")
end

desc 'Run tailor'
task :tailor do
  print_header("Running task: tailor")
  sh "/usr/local/bin/tailor -c ./.tailor"
end


private

def print_header(message=nil)
  puts "#\n# #{message}\n#".cyan
  puts "\n"
end

def print_success(message=nil)
  puts message.green
  puts "\n"
end

def print_warning(message=nil)
  puts "#\n# [WARNING] #{message}\n#".yellow.bold
  puts "\n"
end

def fail_with_message(message=nil)
  puts "#\n# [ERROR] #{message}\n#".red.bold
  exit 1
end
