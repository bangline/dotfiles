require 'rake'
require 'fileutils'

desc "Install the dotfiles"
task :install do
  puts "Creating dotfile symlinks..."
  Dir.glob('symlinks/*') do |file|
  	target = File.join(ENV['HOME'], ".#{filename(file)}")
    if File.exist?(target)
      archive_dir = File.join(ENV['HOME'], '.dotfiles_old')
      FileUtils.mkdir(archive_dir) unless Dir.exist?(archive_dir)
      `mv #{target} #{archive_dir}`
    end
    link_file file
  end
end

def link_file(file)
  `ln -s "#{File.expand_path(file)}" "$HOME/.#{filename(file)}"`
end

def filename(path)
 File.basename(path)
end