desc 'Build'
task :build do
  puts "\n=== Building ==="
  system('mkdir build')
  
  puts "\n*** Building GCC i386 ***"
  system('gcc-4.8 -std=c99 -o build/test_gcc_i386 -arch i386 *.c')
  
  puts "\n*** Building GCC x86_64 ***"
  system('gcc-4.8 -std=c99 -o build/test_gcc_x86_64 -arch x86_64 *.c')
  
  puts "\n*** Building Clang i386 ***"
  system('clang -o build/test_clang_i386 -arch i386 *.c')
  
  puts "\n*** Building Clang x86_64 ***"
  system('clang -o build/test_clang_x86_64 -arch x86_64 *.c')
end

desc 'Test'
task :test => [:build] do
  puts "\n=== Testing ==="
  
  puts "\n*** Testing GCC i386 ***"
  system('build/test_gcc_i386')
  puts '!!! FAILED !!!' if $?.exitstatus != 0
  
  puts "\n*** Testing GCC x86_64 ***"
  system('build/test_gcc_x86_64')
  puts '!!! FAILED !!!' if $?.exitstatus != 0
  
  puts "\n*** Testing Clang i386 ***"
  system('build/test_clang_i386')
  puts '!!! FAILED !!!' if $?.exitstatus != 0
  
  puts "\n*** Testing Clang x86_64 ***"
  system('build/test_clang_x86_64')
  puts '!!! FAILED !!!' if $?.exitstatus != 0
end

desc 'Clean up'
task :clean do
  system('rm -rf build')
end

task :default => [:clean, :test, :clean]
