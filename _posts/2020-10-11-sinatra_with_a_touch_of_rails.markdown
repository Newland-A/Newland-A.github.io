---
layout: post
title:      "Sinatra with a touch of Rails"
date:       2020-10-11 04:55:34 +0000
permalink:  sinatra_with_a_touch_of_rails
---


Hello, 

I created an Web Application for a veternarians office with many vets who have many owners who have many pets. I started off by have four models and a controller for Owners, Vets, Users, Application and Sessions. It vary quickly got to be very confusing as to what belong to what. So I simplified to only having to models one for Users and one for Pets. Users alias vets or owners by using foreign_keys in the models of the application. Which made the relationship a little less complex. My models are listed below:

```
class Pet < ActiveRecord::Base
     belongs_to :vet, class_name: "User" 
     belongs_to :owner, class_name: "User"
end

class User < ActiveRecord::Base
  
  has_many :vets, foreign_key: "vet_id", class_name: "Pet"
  has_many :pets, through: :vets, source: :vet
  has_many :owners, foreign_key: "owner_id", class_name: "Pet"
  has_many :pets, through: :owners, source: :owner
  
  has_secure_password

  validates :username, :email, presence: true
  validates :username, uniqueness: true

  validates_length_of :password, minimum: 8, if: Proc.new { | user | user.password.present? }
end
```

Both models inherit from ActiveRecord:: Base. Has_many through relationships with a source: :attribute.
The has secure password and validations comes from a gem called bcrypt. they encrypt the passwords through a salted hash. Validates checks to make sure the username and email are present and the username is unique. So that only one user can be assigned to each email.

Then the validates_length_of checks to make sure the password is a minimum of 8 characters long. 
The hardest part about using a self join in the sinatra project was iterating through each pet for each owner. It took some serious tinkering and trial and error to find the right combination and right migrations to achieve the connection. I will be using this same model in my rails project and adding onto it. 

I want to add more features to my application that allows the users, (i.e. owners or vets to be able to send messages back and forth and update medications or and medical concerns. Set appointments change and cancel appointments. You would be able to select what vet office you would like to attend or did attend. Also, be able to put in perscription refills and many other features. 

Using self join has been a challenge that I have throughly enejoyed figuring out all the little pieces that make it connect. The Odin Project was a great resource that helped to figure out the relations between the two models. Rake console is an amazing tool to help test code the find what it does and returns. Having multiple terminals open is awesome but can be a bit frustrating when you forget that one has a pry open and nothing will work and you can't figure out why. Then, you have already changed code and done other things to see if that will get it to work. Then, close out of pry to find out that it worked all along. 

To wrap it up, this project has been an absolute awesome experience. 




