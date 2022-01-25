---
title: rails の Controller について
date: 2021-10-26 14:23:28
tags: 
- rails
- ruby
- study
---

## Bootstrap の導入

### Gemfile を編集

`Gemfile` に `bootstrap` を追記する。

```ruby
gem 'bootstrap', '~> 4.0.0'
gem 'mini_racer' # autoprefixer-rails という gem の動作に必要
```

変更を反映するため、 `bundle install` する。

```
$ bundle install
```

`Dockerfile` に記述されているなら `build` する。

```
$ docker-compose build
```

### SCSS を編集する

`./app/assets/stylesheets/` にある `application.css` を `application.scss` に変更して編集する。

```git
- *= require_tree .
- *= require_self
+ @import bootstrap
```

### javascript を編集する

`./app/assets/javascripts/` の `application.js` を編集する。

```git
- //= require jquery
+ //= require jquery3
+ //= require popper
+ //= require bootstrap-sprockets
```

## Bootstrap、SCSS を反映する

`rails-kj/app/views/layouts/` の `application.html.erb` を編集する。

```git
  <body>
+    <div class="container">
      <%= yield %>
+   <div>
  </body>
```

`rails-kj/app/assets/stylesheets/`

`base.scss`
`boards.scss`
