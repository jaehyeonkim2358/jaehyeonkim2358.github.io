namespace :g do
  desc '게시글 생성'
  task :post do
    ARGV.each { |argv| task argv.to_sym }

    file_name = ARGV[1]
    dir = './_posts'
    FileUtils.mkdir_p(dir)
    path = File.join(dir, "#{`date +%Y-%m-%d`.chomp}-#{file_name}.md")
    file_top = "---\ntitle: #{file_name}\ndate: #{Time.now}\ncategories: []\ntags: []\n---\n"
    File.write(path, file_top)

    puts "#{path} was created successfully"
  end
end

def run_and_echo(cmd)
  puts cmd
  result = system(cmd)
  raise "FAIL - `#{cmd}`" unless result
end
task :run do
  begin
    run_and_echo("jekyll serve")
  rescue StandardError => e
    warn "\033[31m#{e}\033[0m"
    exit 1
  end
end
