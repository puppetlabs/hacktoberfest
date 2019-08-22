require 'erb'
require 'base64'
require 'nokogiri'
require 'open-uri'
require 'octokit'

task :default do
  puts 'This rake task will syncronize the contents of the Beginner Friendly Tickets'
  puts 'filter from Jira to issues on this repository. It will ruthlessly close any'
  puts 'issues created here that do not exist in the Jira filter.'
  puts
  puts 'If you would like to update the tickets mirrored here, then simply edit'
  puts 'the filter at https://tickets.puppetlabs.com/issues/?filter=33481.'
  puts
  puts 'Simply run `rake sync` to start the mirror process.'
  puts
  system("rake -T")
end

desc 'Sychronize all issues'
task :sync do
  TOKEN = ENV['GITHUB_TOKEN'] || `git config --global github.token`.chomp

  if TOKEN.empty?
    puts "You need to generate a GitHub token:"
    puts "\t * https://help.github.com/en/articles/creating-a-personal-access-token-for-the-command-line"
    puts "\t * git config --global github.token <token>"
    puts
    puts "Export that as the `GITHUB_TOKEN` environment variable or put it in your ~/.gitconfig."
    exit 1
  end

  begin
    client = Octokit::Client.new(:access_token => TOKEN)
  rescue => e
    puts "Github login error: #{e.message}"
    exit 1
  end

  source = 'https://tickets.puppetlabs.com/sr/jira.issueviews:searchrequest-xml/33481/SearchRequest-33481.xml?tempMax=1000'
  repo   = 'puppetlabs/hacktoberfest'

  gh_issues   = client.list_issues(repo)
  jira_issues = Nokogiri::XML(URI.parse(source).read).xpath('//item').map do |issue|
    if issue.at_xpath('project').content == 'Modules'
      component = 'Modules'
    else
      component = issue.at_xpath('component').content rescue nil
    end
    description = issue.at_xpath('description').content rescue nil
    {
      :title       => issue.at_xpath('title').content,
      :link        => issue.at_xpath('link').content,
      :created     => issue.at_xpath('created').content,
      :updated     => issue.at_xpath('updated').content,
      :component   => component,
      :description => description,
      :labels      => issue.xpath('labels/label').map {|label| label.content },
    }
  end

  # find issues in Jira that don't exist in GitHub
  create = jira_issues.reject do |jira|
    gh_issues.find {|gh| gh[:title] == jira[:title]}
  end

  create.each do |issue|
    puts "+ Creating issue: #{issue[:title]}"
    body = ERB.new(File.read('_issue_description.erb')).result(binding)
    client.create_issue(repo, issue[:title], body, :labels => "hacktoberfest,#{issue[:component]}")
  end


  # find issues in GitHub that don't exist in the Jira filter
  destroy = gh_issues.reject do |gh|
    jira_issues.find {|jira| jira[:title] == gh[:title]}
  end

  destroy.each do |issue|
    puts "- Closing issue: #{issue[:title]}"
    client.close_issue(repo, issue[:number])
  end
end
