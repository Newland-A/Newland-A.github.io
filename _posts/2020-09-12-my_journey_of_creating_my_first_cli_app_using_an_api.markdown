---
layout: post
title:      "My journey of creating my first CLI app using an API!"
date:       2020-09-12 22:26:51 -0400
permalink:  my_journey_of_creating_my_first_cli_app_using_an_api
---


Hello, I am writing this blog to talk about some of the struggles and some of the celebration moments of creating your first CLI app. 

I am doing my project on OuterSpace. It is very limited and very versatile at the same time. There is so much information. Trying to find what to include? and what to exclude? has been a challenge. My API is returning a massive amount of data and I've had trouble finding a solution that limits it without removing planets from the apps list.

This has been a fun experience so far of truely seeing how all of the pieces work together. I now know how to import an API and use the information that is given. 

Why I choose to do a project on the Solar System! My daughter and I have always stay-up late just to track the moon and look at the stars her favorite constellation is O'rians Belt. I am going to try and include information on the different constellations as well. Scraping websites and using an API seems to be my best bet to get all the information that I want to include. There isn't an API that include all known information about OuterSpace. Maybe, I will create one. I have learned a lot even in just the beginning stages. There is so much more to learn. It has been a learning experience for my daughter as well. She knows that I am doing a project on the Solar System and is doing research to help me get information about the different thing out there.

RestClient is a simple, Python + wxWidgets Desktop application for talking to RESTful web services. It is designed to fill a gap in existing offerings by offering support for GET/POST/PUT/DELETE, making it a useful tool when exploring RESTful web services which use a wider range of HTTP verbs.

I found a restful API and used the restclient gem to be able to use JSON and retrieve my data from the API.

I started out by making my retrieve method 

```
def self.retrieve_planets
    # response = RestClient.get('https://api.le-systeme-solaire.net/rest/bodies/')
    response = RestClient.get('https://api.le-systeme-solaire.net/rest/bodies/{id}')
    planet_hash = JSON.parse(response.body, symbolize_names:true)
    planets_array = planet_hash[:bodies]#[:name]

    planets_info = planets_array.collect { |planet| Planets.new(planet)}
    
    #binding.pry
  end
	```
	
	I used binding.pry to test my app as I was building it to see if each piece was working the way I wanted it too.
	
	Binding.pry needs to be required in your run file and then you can place a binding where needed.
	
	I then moved on to creating my planets class that holds my planets. Next, I created my details class that holds the details of all the planets. 
	
	My hurdle is finding a way to limit the output of my API in the CLI.
	
	From here this is where the journey starts the challenges.
	
	I started out doing my project on the solar system. I very quickly learned that a API for what I was wanting to do was not existent. It would require several API's or to combine scraping and many API's. It quickly became too much for one person in 7 days. So, After 3 starts on trying to create a app with API for the solar system. I was 4 days in. I started to get worried that I wasn't going to be able to finish it time. I decided it was time to find another API and a different topic.
	
	I found another API that had amazing documentation and seemed to be simple enough to create something awesome in only 3 days remaining. The first day of the API was going good going through the documentation and creating an API key and API secret. After creating these I was supposed to use them to get a token using a curl command. I was unable to get the token, because of a 401 error. A 401 error is an error that states you API key and secret maybe wrong or your using an expired url. So, I got my lead involved on trying to solve the issues. After, I had exhausted google and the documentation. She was unable to find a reason that it wasn't working either. She then got another lead involved and all of us spent an hour in a zoom call trying to determine what was wrong. Meanwhile, I was waiting on a response for the developers for the API that I had sent earlier that day. I didn't know if I was going to be able to get a response from them in time to continue the project. So, once again. After a whole day of trying to get a token. I knew I had to find yet another topic and another API. 
	
	update: PetFinder API  I finally got a response back from the API developers and we were able to fix the issue. In my spare time I will finish this project. It is a really good API. Don't use the curly braces { } in the curl command they are ment to be place holders. Reach out to the developers of the API their wonderful and very helpful, if you use this API.
	
	So, I then found a API on the Game of Thrones and this is where I start to see a glimmer of hope again. It was a simple API that listed characters, information on those characters and the different houses. I proceeded in starting over once again. I only had 2 days left at this point. After, creating files and doing my research and learning how to fix so many issues in such a short period of time. I was able to fully create a working app in a day. 
	
	Some of the issues I had was not being able to find a good enough API til the end. Github did not want to let me link my files and my github. Every API I choose did not like the `gem bundler install'. Here is the beginning code for my GOT app.
	
	```
	class API

  def self.create_characters
    #goes out and gets the information from the API
    response = RestClient.get('https://anapioficeandfire.com/api/characters?page=3&pageSize=25')
    # binding.pry
    #returns that information in a parsed hash sy
    got_hash = JSON.parse(response.body, symbolize_names:true)
    #selects the main key in the hash
    # char_array = got_hash[:name]
    #then iterates through the hash and returns the elements
    got_hash.each do | character |
      url = character[:url]
      name = character[:name]
      CHARACTERS.new(name, url)
   #binding.pry true
    end
  #binding.pry
  end

  #binding.pry

  def self.character_list(character)
    response = RestClient.get(character.url)
    char_hash = JSON.parse(response.body, symbolize_names:true)
    # character.name = char_hash[:name]
    # binding.pry
    character.gender = char_hash[:gender]
    character.culture = char_hash[:culture]
    character.born = char_hash[:born]
    character.titles = char_hash[:titles]
    character.aliases = char_hash[:aliases]
   # binding.pry
  end
 
  def self.create_houses
  #goes out and gets the information from the API
    response = RestClient.get('https://anapioficeandfire.com/api/houses?pageSize=25')
  #returns that information in a parsed hash, symbolize turns all the keys a different color for easier readability
    house_hash = JSON.parse(response.body, symbolize_names:true)
  #selects the main key in the hash
    # house_array = house_hash[:name]
  #then iterates through the hash and returns the elements

  #it does not like the collect key word, Try to find a fix in the morning after a break.
    house_hash.each do |realm|
      url = realm[:url]
      name = realm[:name]
      HOUSES.new(name, url)
    end
#binding.pry
  end
	```
	
	
	It includes some of the comments that I made while creating the app and shows some insight on how I was able to fix some of the bugs I had with the program. 
	
	If you make changes in you github, say something comes to you and you know the fix but dont have your computer but you have you phone and can get to github. You can make changes just remember to do a git pull when you get back to you computer if not it can cause merge issues. Then you have to merge using the working tree. Then do another git commit -m and git push after you have merged the files.
	
	Since, I started 6.times. I have six 30 minute long coding videos. 
	
	What I learned during this process is always believe in your self. Never be afraid to ask for help. 
	puts "SAY I DONT KNOW IF YOU DON't KNOW"
	Trial and error is an amazing way to learn new things. keep track of the things you have tried. You can clean up your code later. Know  that your never done refactoring because everything can change and be updated.
	
	Thank you for reading. I appreciate any feedback. On the blog post or the code. Here to keep growing and learning with everyday. Good luck with your journey's everyone.
	
	
