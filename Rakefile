desc "sync gemfile, "
task :get do
  filepath = 'Gemfile.lock'

  sh "cp ../*-v2/#{filepath} ./"

  IO.write(filepath, File.open(filepath) do |f|
      f.read
        .gsub(/(?=)([a-z0-9\:\-]*@)(?=github.com)/, '')          # gh repo credentials
        .gsub(/(?<=github.com\/)([a-zA-Z]{12})(?=\/)/, 'bluta')  # gh repo names
    end
  )
  sh 'git add Gemfile.lock'
  sh 'git diff master'
end


