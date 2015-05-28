## Welcome to the rails template
This project is a bower package, which can be included into any rails app, in order to copy standard files across when starting a new project. The idea is that the project will grow to include templates for other types of applications too.

## Step 1 - Create a new rails app
If your not familiar with Ruby on Rails, check out the [install rails](http://installrails.com/) site to get setup.

Once your setup, create yor new app. The following command creates a new app called 'myApp', but turns off the asset pipeline, and removes turbolinks.

```
rails new myApp --skip-sprockets --skip-turbolinks
```

## Step 2 - Dependencies
This section can be skipped if you're already setup with NodeJs, Grunt and Bower.
### Node.js (npm)
```
brew install node
```
### Grunt CLI
```
npm install -g grunt-cli
```
### Bower
```
npm install -g bower
```

## Step 3 - Initialise and Install project dependencies
### Initialize Node
```
npm init
* Press enter until the end *
```
### Install grunt packes
* Grunt
* Grunt-contrib-less
* Grunt-contrib-uglify
* Grunt-contrib-copy
* Grunt-contrib-concat

Copy the full code block below, and paste in your terminal.
```
npm install grunt --save
npm install grunt-contrib-less --save
npm install grunt-contrib-uglify --save
npm install grunt-contrib-copy --save
npm install grunt-contrib-concat --save
```

## Step 4 - Setup Bower to include this repo
The final grunt command will generate you a bower.json, so you don't need to init one yourself
```
bower install https://github.com/neilwilliams/rails-template.git#master --save
```

## Step 5 - Run the package, to create the standard files
This assumes that your default bower directory is at the root of your application.
```
grunt --gruntfile bower_components/rails-template/Gruntfile.js --base ./
```

## Step 6 - Tweak rails config
### Setup locales
* Remove the en.yml file from config/locales
* Add the following to you application.rb config file:  
```
config.i18n.load_path += Dir[Rails.root.join('config', 'locales', 'english', '*.{rb,yml}').to_s]
```
There maybe something similar in there already, commented out. You can overwrite the existing line if it exists.

Your all set! Run your app and you should see it has been setup for you. You will also have your own Gruntfile.js so you can run 'Grunt' to generate any modifications you make to your assets.

* Custom LESS (css) code should be placed in app/assets/stylesheets/main.less
* Custom JavaScript should be placed in app/assets/javascripts/main.js