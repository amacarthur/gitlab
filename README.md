# Gitlab

[![Build Status](https://secure.travis-ci.org/NARKOZ/gitlab.png)](http://travis-ci.org/NARKOZ/gitlab)

Gitlab is a Ruby wrapper for the [GitLab API](https://github.com/gitlabhq/gitlabhq/tree/master/doc/api#gitlab-api).

## Installation

Install it from rubygems:

```sh
gem install gitlab
```

Or add to a Gemfile:

```ruby
gem 'gitlab'
# gem 'gitlab', :git => 'git://github.com/NARKOZ/gitlab.git'
```

## Usage

Configuration example:

```ruby
Gitlab.configure do |config|
  config.endpoint       = 'https://example.net/api/v2' # API endpoint URL (required)
  config.private_token  = 'qEsq1pt6HJPaNciie3MG'       # user's private token (required)
  config.user_agent     = 'Custom User Agent'          # user agent, default to 'Gitlab Ruby Gem [version]' (optional)
end
```

Usage examples:

```ruby
# set an API endpoint
Gitlab.endpoint = 'http://example.net/api/v2'
# => "http://example.net/api/v2"

# set a user private token
Gitlab.private_token = 'qEsq1pt6HJPaNciie3MG'
# => "qEsq1pt6HJPaNciie3MG"

# list projects
Gitlab.projects(:per_page => 5)
# => [#<Gitlab::ObjectifiedHash:0x000000023326e0 @data={"id"=>1, "code"=>"brute", "name"=>"Brute", "description"=>nil, "path"=>"brute", "default_branch"=>nil, "owner"=>#<Gitlab::ObjectifiedHash:0x00000002331600 @data={"id"=>1, "email"=>"john@example.com", "name"=>"John Smith", "blocked"=>false, "created_at"=>"2012-09-17T09:41:56Z"}>, "private"=>true, "issues_enabled"=>true, "merge_requests_enabled"=>true, "wall_enabled"=>true, "wiki_enabled"=>true, "created_at"=>"2012-09-17T09:41:56Z"}>, #<Gitlab::ObjectifiedHash:0x000000023450d8 @data={"id"=>2, "code"=>"mozart", "name"=>"Mozart", "description"=>nil, "path"=>"mozart", "default_branch"=>nil, "owner"=>#<Gitlab::ObjectifiedHash:0x00000002344ca0 @data={"id"=>1, "email"=>"john@example.com", "name"=>"John Smith", "blocked"=>false, "created_at"=>"2012-09-17T09:41:56Z"}>, "private"=>true, "issues_enabled"=>true, "merge_requests_enabled"=>true, "wall_enabled"=>true, "wiki_enabled"=>true, "created_at"=>"2012-09-17T09:41:57Z"}>, #<Gitlab::ObjectifiedHash:0x00000002344958 @data={"id"=>3, "code"=>"gitlab", "name"=>"Gitlab", "description"=>nil, "path"=>"gitlab", "default_branch"=>nil, "owner"=>#<Gitlab::ObjectifiedHash:0x000000023447a0 @data={"id"=>1, "email"=>"john@example.com", "name"=>"John Smith", "blocked"=>false, "created_at"=>"2012-09-17T09:41:56Z"}>, "private"=>true, "issues_enabled"=>true, "merge_requests_enabled"=>true, "wall_enabled"=>true, "wiki_enabled"=>true, "created_at"=>"2012-09-17T09:41:58Z"}>]

# initialize a new client
g = Gitlab.client(:endpoint => 'https://api.example.com', :private_token => 'qEsq1pt6HJPaNciie3MG')
# => #<Gitlab::Client:0x00000001e62408 @endpoint="https://api.example.com", @private_token="qEsq1pt6HJPaNciie3MG", @user_agent="Gitlab Ruby Gem 2.0.0">

# get a user
user = g.user
# => #<Gitlab::ObjectifiedHash:0x00000002217990 @data={"id"=>1, "email"=>"john@example.com", "name"=>"John Smith", "bio"=>nil, "skype"=>"", "linkedin"=>"", "twitter"=>"john", "dark_scheme"=>false, "theme_id"=>1, "blocked"=>false, "created_at"=>"2012-09-17T09:41:56Z"}>

# get a user's email
user.email
# => "john@example.com"
```

For more information, refer to [documentation](http://rubydoc.info/gems/gitlab/frames).

## License

Released under the BSD 2-clause license. See LICENSE.txt for details.
