---
layout: post
title:      "Hello Rails, Half Way Point!"
date:       2020-11-09 14:44:27 -0500
permalink:  hello_rails_half_way_point
---



Hello, What were some of the struggles with creating this project? Some of the major accomplishments? How much harder was it to create the rails project than Sinatra? 

Sinatra was complicated trying to use a self join. When I switched it over to rails it made things a lot easier because of how rails takes charge and knows that things are supposed to be ralated. 

Using partials is an awesome way to have lots of code in multiple places but you only had to write it once. the render file name. 

I used bootstrap and bootswatch with popper.js to create my css basic styling. if you have a basic understanding of how html, css, and javascript work. Bootstrap is an amazing tool to get css up and running quickly with a little google action.

I created my own validations for the models in this project. I have set custom validations for my nested animal attributes for my users.  My relationships are as follows. 
```
**Animal**
  has_many :animal_companies
  has_many :companies, through: :animal_companies

  validates_presence_of :name, :gender, :species

  belongs_to :user

**AnimalCompanies**
belongs_to :animal
belongs_to :company

**Company**
has_many :animal_companies
has_many :animals, through: :animal_companies

**User**
has_many :owners, class_name: "User", foreign_key: "vet_id"
  belongs_to :vet, class_name: "User", optional: true
 
  has_many :animals, dependent: :destroy

  accepts_nested_attributes_for :animals, reject_if: proc { |attributes| attributes['name'].blank? ||    attributes['gender'].blank? || attributes['species'].blank?}

  has_secure_password

  validates :username, :email, presence: true, uniqueness: true
  validates_length_of :password, minimum: 8, if: Proc.new { | user | user.password.present? }
```

This project has been the most fun to create so far, because it really shows how all the pieces fit together. It has been a little challenging try to figure out how everything transfer over to fully rails. Sinatra was more complicated in my opinion by itself. Routes are simple to figure out. Resources generate the routes for you unless you need to specify a certain route. Creating nested routes make linking different pages together much easier. The hardest part about this project has been omniauth. Omniauth once figured out is amazing it basically allows for the user to be able to sign in using other accounts such as google, facebook, github, and many others. Your gem file needs to require omniauth. then your app secret and keys need to be kept in a .env file and referenced in your config initializer file. Then you create the link on the pages you want it to be located or in a layout file with conditions for if the user is logged in or not. Which helps to keep your code DRY. DRY stands for DON'T REPEAT YOURSELF. This has been an amazing experience going through bootcamp and learning as much as I have there is still a long road ahead to become a professional engineer. With everyday I gain new knowledge and get one step closer to the goals I ahve set. I have made a lot of resources for learning new things and people to grow with and learn from. This is the halfway point. I can't believe I have already came this far and so excited for everything that is too come.
