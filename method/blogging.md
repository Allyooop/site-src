# Adding a blog

Let's create a blog.

Luckily Middleman comes with an offical package that you can easily add in to provide the bloging framework.

In your gemfile add the following:

```ruby
gem "middleman-blog"
```

Run 

```ruby
bundle install
```

If you have already built your run:

```bash
middleman init --template=blog
```

which won't override any files but will quickly create the required sitemap.xml file


In your ```config.rb``` file add the following:
```ruby
activate :blog do |blog|
  blog.permalink = "blog/{year}/{title}.html"
end
```