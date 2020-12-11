---
layout: post
title:      "Have a Happy Holiday JS"
date:       2020-12-11 07:30:02 -0500
permalink:  have_a_happy_holiday_js
---


Hello, My name is Amy Newland. 

I have completed one more step towards my goals of becoming a Software Enginner. This blog post is about my Rails with JavaScript Project. I create an application for children. It the holiday season and many kids are a little down so to try and spread some cheer for the holiday season. I created an app that allows children to send Santa their Wish. Once their wish has been created or made Santa will delete their Wish. I have had an amazing time created this project. It has been fun, exciting and challenging. 

JavaScript is amazing in so many ways. There is no one right way to write JavaScript. Theres definitely a few wrong ways. I enjoyed that there was little requirements for this project, it really gave me the opportunity to explore the language and test different ways of writing JS. So, I could find my own path in the language. The curriculum was a rough path of material to get through. None the less. I have succeed in taking the first steps to learning another new language. I am excited about being near the end of the course and getting ready to start my  new career. 

I may not be the best at creating an application from scratch, I have definitely learned a lot and ready to see what new things I will be learning everyday. I enjoy that the career path is so wide spread there is aalways something new to learn and enhance your skills as a person and a developer. 

Well on to more about my project. With the blog I am going to give a simple breakdown of beginning to never perfected. There is always something you can add or change. No application is truely complete or done. 


For this project., the first steps is to setup up the files. You want to create a main directory. with in that directory is to folders. One is for the backend (your rails side of the application). The other is for your frontend (the javascript, html, css side of the application). 

When creating the front end to start you want to add a README.md file so when you link it to github you will be able connect and push the file. Here is a link to some information about linking the two if you need a reminder or some help. https://kbroman.org/github_tutorial/pages/init.html I did not write this information. It was just something I found useful when starting out. 

The next step is to setup your rails side of the application useing `rails new project_name and any flags you might want to pass in` I used --api --no-test-framework. I used the --api flag because I didn't want rails creating all of the views and excess code that wasn't going to be used with this project. Then, after you create the new application. You set up the models and controller and migrations. Either by hand or you can use Scaffold. Scaffolding is awesome for a quick setup if you understand how everything is connected and put together. If you are still a little hazy on how everything is working I recommend setting up the application by hand. Rails new will automatically do git init for you to create a new git repository for you. Unlike when you created your frontend you had to manually do git init. 

The next steps would be to go to git hub and generate a repository for your front end and run the commands provided. Then, create a github reposiitory for your backend. After, you have both repositories link to your files. I recommend putting a link in your front end README for your backend and vice versa. These steps should take about 30 minutes or less. After you have completed all of this. Your all set to start building your version of a wonderful application. 

BEWARNED be paitent with yourself. When you are learning JavaScript. Why well because JavaScript can be a complicated language because there is so many different way to do things. 

After I got all of this completed. I started adjusting my migrations for the information I wanted to take in I created two models. One for lists and one for list_items. Wish_List has_many Wish_Items. My list consists on the name delivery_date and the items count. These can all be adjusted as desired. My items consist of a name color height weight description price and a link to the photo or where it can be got. After my migrations were set as how I wanted to begin creating my application.

Its then time to start adding your JS to your file your index.html can have elements in it to help make things a little less confusing if your starting out. But, It is not neccessary other than a BASIC html setup. Start by setting your URLS to variables to make it easier for fetchs instead of having to write the whole url every time. Then, start adding a single element at a time. I do not recommend setting all of your elements at once because it will make things confusing and out of order and will make it more challenging to have things appear in the order that you would like. 

Once you have you basic html and have set your variables and created your first element start creating your fetch requests to the backend of the application to retrieve your data. and trying to have it appear on the element you created for it. Oh yeah, I forgot one important thing if you would like to have data to test things in your application. You will need to create your seed data as well. But, again its not absolutely neccessary. It can also take quite some time to create your seed data depending on your objects and information you want to take in or display. 

Once you are getting the information from the backend you are ready to start making it appear to the DOM (DOCUMENT OBJECT MODEL). For the JS project you will need to create at least 3 of the CRUD actions using fetch requests. I used READ CREATE and DELETE. As you are going through your project and building it feature by feature. I recommend that you do your css as you go along. Use id's on everything you can to make grabbing pieces of information and setting your css as simple as possible. 

I am going to display some of my fetch requests here because that maybe some help to see how they should be done if you need help. But, again there is many ways to do eveything in JS. 

`
// read the information your getting from your backend
static readList() {
    fetch('http://localhost:3000/wish_lists')
    .then(resp => resp.json())
    .then(wish_lists => {
      wish_lists.forEach(wish_list => {
        const { id, title, item_count, delivery_date } = wish_list
        new WishList(id, title, item_count, delivery_date )
      })
    })
  }

// posting form to the dom and grabbing the attributes inputs, clearing form after submission

  static createList(e) {
    e.preventDefault()
    let list = {
      'title': e.target.title.value,
    };
    fetch(WISHLIST_URL, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify(list)
    })
    .then(resp => resp.json())
    .then(wish_lists => {
      const { id, title} = wish_lists
      // debugger
      new WishList(id, title )
      renderNestedForm(id, title)
      document.getElementById('nested-form').addEventListener('submit',  API.createItems
      )
      document.getElementById('nested-form').reset()
      })
  }
	`
	
	The above fetch requests the first one reads my information the second one takes it in and sets the values to a variable and tells the fetch request that it is a post fetch destructures the attributes that are coming in, creates a new object for the information taken in then renders the form to take in the information and after the form is submitted it will clear the form of the information provided.
	
	I hope this helped to get an Idea of how to begin your Rails With JavaScript Project. I wish every a great Holiday Season. Good luck to everyone starting a new journey soon. 
