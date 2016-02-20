# the post is created compatible with jekyll

WORK_DIR = 'src'
EDITOR   = ENV['EDITOR'] || 'gvim'

def filename file
	Time.now.strftime('%Y-%m-%d-') + file.split.join('-') + '.md'
end

desc "create file under LANG"
task :new, %i[lang title] do |t, args|
	lang  = args.lang
	title = args.title
	file  = "#{WORK_DIR}/#{lang}/#{filename title}"
	mkdir_p "#{WORK_DIR}/#{lang}"
	touch file
	File.open(file, "w") do |f|
		f.puts "---"
		f.puts "layout: post"
		f.puts "title: \"#{title}\""
		f.puts "date: #{Time.now.strftime('%Y-%m-%d %H:%M:%S')}"
		f.puts "categories: [\"#{lang}\"]"
		f.puts "tags: []"
		f.puts "---"
		f.puts
	end
    system "#{EDITOR} #{file}"
end

desc "push to github"
task :push, %i[msg] do |t, args|
	msg = args.msg || "updated at #{Time.now.utc}"
	system "git add ."
	system "git commit -m \"#{msg}\""
	system "git push origin master"
end
