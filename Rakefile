desc "sync gemfile, "

task default: :get
task :get do
  filepath = 'Gemfile.lock'

  sh "cp ../*-v2/#{filepath} ../*-v2/.ruby-version ./"

  IO.write(filepath, File.open(filepath) do |f|
      f.read
        .gsub(/(?=)([a-z0-9\:\-]*@)(?=github.com)/, '')          # gh repo credentials
        .gsub(/(?<=github.com\/)([a-zA-Z]{12})(?=\/)/, 'bluta')  # gh repo names
    end
  )
  sh 'git add Gemfile.lock .ruby-version'
  sh 'git diff master'
end


