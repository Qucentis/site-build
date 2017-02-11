desc "Publish"
task :publish do
  message = 'Commit by script'
  `mkdir -p _build`
  `jekyll build -d "_build"`

  Dir.chdir('_build') do
    if nothing_to_commit?
      puts "Nothing new to publish!"
    else
      `git add .`
      `git commit -m '#{message}'`
      `git push 2>&1`

      puts "Published"
    end
  end
end

def nothing_to_commit?
  git_status = `git status`
  !!(git_status =~ /nothing to commit,/)
end
