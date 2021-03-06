# cap-3-rails
capistrano 3 rails config template


#### 使用

#### 准备


一台新的机器上，先

```
group :development do
  gem 'capistrano', '~> 3.1'
  gem 'capistrano3-rails-config'
end
```

```
require 'capistrano3-rails-setup'
```

生成各种模板:

```
$ bundle exec rails g capistrano:monit:template
```

模板上传：

```
bundle exec cap production setup
```

#### 对该服务器环境进行配置，主要是db和配置串：

```
$ mv database.example.yml database.yml
$ mv secrets.example.yml secrets.yml
```

#### 然后进行deploy

```
$ cap prod deploy
```

## 其它操作

#### Unicorn 相关操作

```
$ cap prod unicorn:start
$ cap prod unicorn:restart
$ cap prod unicorn:stop
```

#### Nginx 相关操作

```
$ cap prod nginx:start
$ cap prod nginx:restart
$ cap prod nginx:stop
```

#### Monit 

```
$ cap prod monit:status  # shows the output of running `monit status` on the server
$ cap prod monit:start   # sends a start signal to all monitored processes
$ cap prod monit:stop    # sends a stop signal to all monitored processes
$ cap prod monit:restart # sends a restart signal to all monitored processes
```


#### Sidekiq

```
no
```


#### Redis

```
sss
```
## 其它备注

因使用 `capistrano3-unicorn`  和 `capistrano3-nginx` ，所以之前写的 `nginx.rake` 和 `unicorn.rake` 不再使用，`unicorn_init.sh` 也不再使用。



REF::
---
- https://github.com/louishouette/capistrano-monit-recipes
- https://github.com/TalkingQuickly/capistrano-3-rails-template
- https://github.com/naps62/capistrano3-monit
- https://github.com/seuros/capistrano-sidekiq