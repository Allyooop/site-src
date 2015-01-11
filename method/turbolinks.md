# Add Turbolinks to your project

Let's add turbolinks to our project.

If you have built a Rails project before you may have used turbolinks before.

Essentially it is a very lightweight javascript tool that makes your html act like a single page application. That is, Turbolinks only loads your CSS JS etc. once and lets your users navigate around your much faster because only the HTML that needs to be loaded, is loaded.

There are a few things to watch out for when using it with other Javascript that waits on something needing a full page load because Turbolinks essentially doesn't reload your page, but rather replaces the the bits of the page that need to be replaced. We'll cover those "gotchas" in due course. There are plenty of work arounds but if you don't want to use the library feel free to skip this section.

## Update your gemfile

The first thing we need to do is update our gemfile. Crack that open and include the following:

```ruby
gem "turbolinks", require: false
```

The ```require: false``` but is just something that you have to override for Middleman due to certain quirks with gems being made for Rails and expecting files to be in a specific folder. By saying the library is not required, you are just saying "if it is not in that Rails folder, don't worry about it!".

Make sure you install the gem by running:

```
bundle install
```

Next we need to load it up into our layout.

First we need to include it via a javascript file.

Let's create one for that purpose called ```app.js``` and place it in the javascripts file.

I've also deleted the all.js file. If you don't want to delete it, make sure you delete the sprocket ```require``` statement.

In our ```app.js``` file, add the following to the top:

```javascript
//= require turbolinks
```

Now, in our ```layout.erb``` make sure you delete the call to ```"add"``` and replace it with ```"app.js"``` like so:

```erb
<%= javascript_include_tag  "app" %>
```

