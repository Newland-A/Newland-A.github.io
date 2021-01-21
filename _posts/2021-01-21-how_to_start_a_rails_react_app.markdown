---
layout: post
title:      "How to Start a Rails/React App"
date:       2021-01-21 15:48:26 +0000
permalink:  how_to_start_a_rails_react_app
---


Hello Everyone, 

I am writing this blog post in regards of my final project. I decided to tackle 2 objectives with this one. Not only is it my final project, it is also my portfolio. I created a Ruby on Rails generated back-end with a postgresql database. My front-end is created with React.js. 

There is not much good documentation about React. This is one of the best resources, I have found https://reactjs.org/. It gives a tutorial and detailed information on everything React. If you are interested in learning React. I recommend starting here. 

For a React front-end to create the back end is fairly simple. If you are wanting to use third-party authentication (OAuth) in your project. I wouldn't recommend using the --api flag with rails new. Before any project, Double check that you have the required software and gems and frameworks installed. Use this command to setup a rails app with postgresql database.

`rails new myapp --database=postgresql`

After you have generated your application. The first things you're going to want to do is. Check your gemfile for the rack-cors gem. This gem allows web applications to make cross domain AJAX calls without using workarounds such as JSONP. After, you have added this gem to your gemfile you will want to go into your config/initializers folder and go into your cors.rb file and adjust what servers can make what kind of AJAX calls. 

The next task you will want to accomplish is running `bundle install` within your terminal. I also added pry `gem 'pry'`, faker `gem 'faker'`, and bcrypt ` gem 'bcrypt', '~> 3.1.7' ` to my gemfile. Bcrypt is used with activerecord to help in the process of storing passwords securely.

The next step is to use scaffold to generate your models controllers and routes or to write them in by hand. Once, you have an idea for your porject. Then run rails db:create to start the database. If you use scaffold it will automatically generate.

Next, Go into your controllers and make sure your app is rendering the json on the back end example `render json: @campgrounds.as_json(include: {reviews: {only: [:id, :title, :description, :score]}})`

This makes sure that react wont bork out and you are using react to render on the frontend instead of using your backend views.

Once you have setup your backend and got basic idea of what you are wanting to create. It's time to start on your front end. Within the same folder that you generated your backend run the command `npx create-react-app my-app` and it will set everything up for you. Make sure to connect both folders to github. Make your initial commits. 

Now that you have your backend and front end set up and folders organized make sure that everything goes into your /src folder. I started by creating a components, Containers, and Redux folders. Inside of the Components file. You can seperate each feature out into its own folder or all together. 

The components folder is for all of the individual pieces that are being imported into the parent components.

The Containers folder is for your main component (parent component). My containers folder consists of Blog, Campground, Comments and Reviews Containers. Where the main html(jsx) is generated for the rendering of your components.

The Redux folder consists of two more folders one for actions and one for reducers. 

Once, You have your main folders setup start adding components one at a time. Do not try and put everything in at once. Add as you need it. I hope that this helps. If anyone has any questions or wants to connect. I can be reached at ajn252@gmail.com or let's connect https://www.linkedin.com/in/amy-newland-developer/


