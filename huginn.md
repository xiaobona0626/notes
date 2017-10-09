# Huginn  
https://github.com/huginn/huginn

# Installation MACOS
** 
```
$ brew install ruby
$ brew link --overwrite ruby
$ gem install rails

$ brew install v8
$ brew install v8@3.15
$ gem install libv8 -v 3.16.14.19 -- --with-system-v8
$ gem install therubyracer -v '0.12.3' -- --with-v8-dir=/usr/local/opt/v8@3.15
$ bundle exec rake db:create -- --with-readline-dir=/usr/local/Cellar/readline/7.0.3_1/
$ bundle exec rake db:migrate
$ bundle exec rake db:seed
$ bundle exec foreman start
```
