require 'rake/clean'

CLEAN.include("**/*.pyc")

PythonInterpreter = ENV.has_key?('PYTHON') ? ENV['PYTHON'] : 'python'
RubyInterpreter   = ENV.has_key?('RUBY')   ? ENV['RUBY']   : 'ruby'

def pythonTest(name: nil,interpreter: PythonInterpreter)
  cmd = "cd python; [[ ! -f testcdo.py ]] && ln -s -f cdo.py testcdo.py ; PYTHONPATH='.' #{interpreter} test/test_cdo.py"
  cmd << " CdoTest.#{name}" unless name.nil?
  cmd
end
def rubyTest(name: nil,interpreter: RubyInterpreter)
  cmd = "cd ruby; #{interpreter} test/test_cdo.rb"
  cmd << " --name=#{name}" unless name.nil?
  cmd
end

desc "execute one/all test(s) with python2"
task :testPython2, :name do |t,args|
  sh pythonTest(name: args.name,interpreter: 'python2')
end

desc "execute one/all test(s) with python3"
task :testPython3, :name do |t,args|
  sh pythonTest(name: args.name,interpreter: 'python3')
end

desc "execute one/all test(s) with python or the given env: PythonInterpreter"
task :testPython, :name do |t,args|
  sh pythonTest(name: args.name)
end

desc "execute one/all test(s) with ruby or the given env: RubyInterpreter"
task :testRuby, :name do |t,args|
  sh rubyTest(name: args.name)
end
