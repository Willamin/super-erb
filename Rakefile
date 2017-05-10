require 'fileutils'

task :ruby do
  exec('ruby hello.rb')
end

task :erb do
  exec('erb hello.erb')
end

task :both do
  exec('ruby -e "$(erb hello.rb.erb)"')
end

task :fib do
  exec('ruby -e "$(erb fib.rb.erb)"')
end

task :full do
  # file = "fib.rb.erb"
  file = "four.rb.erb.erb.erb.erb"
  Dir.mkdir('build') unless Dir.exist?('build')
  FileUtils.cp(file, "build/#{file}")

  newfile=""

  while /\.erb$/.match(file) do
    newfile = /(.*)\.erb$/.match(file)[1]
    puts "#{file} -> #{newfile}"
    a = `erb build/#{file} > build/#{newfile}`
    file = newfile
  end
end
