
## Meme Generator

- ***Part 1 Due: 10 Oct***
- ***Part 2 Due: 10 Oct***
- ***Part 3 Due: 17 Oct***

### Overview

Using the existing code from the vagrant server I uploded to slack or [HERE](https://github.com/rugbyprof/4443-Internet-Programming/blob/master/Assignments/05-Meme_Generator/meme_generator.zip) add additional functionality to make each meme look much better.

### Remember

- ***Host*** = Your pc or laptop
- ***Guest*** = Vagrant instance 

- Start your vagrant box (the guest): `vagrant up`
- Log into your vagrant box `vagrant ssh`
- Start your "api": `cd /vagrant_data/scripts/ && python api.py`
- Check everything is running by browsing to the following (on the host):
    - localhost:8080   (meme web page)
    - localhost:5050   (api)

### Folder Structure

- &#128187; meme_generator (vagrant container)
    - &#128193; var/www/html/
        - &#128193; images
        - &#128193; memes
    - &#x21b3; index.html
    - &#128193; css
        - &#x21b3; bootstrap.min.css
        - &#x21b3; some.main.css
    - &#128193; js
        - &#x21b3; bootstrap.min.js
        - &#x21b3; jquery.min.js
    - &#128193; scripts
        - &#x21b3; compare_image.py
        - &#x21b3; meme-api.py
        - &#x21b3; meme-creator.py
        - &#x21b3; seed_db.py

### Part 1
Due: 10 Oct By Class time.

***Meme Route***

Update the `meme/new` route in `meme-api.py` to create a meme. Your route will receive posted data similar to the following:

```json
{
	"top_text" : "You smell good",
	"bot_text" : "when your sleeping...",
	"style_info" : {
		"text-color" : [
			0,
			0,
			0
		],
		"text-size" : 24,
        	"font" : "Ultra-Regular.ttf"
	},
}
```

And it will insert into our mongo db a document based on the following example:

```json
{
	"_id" : 3,
	"top_text" : "You smell good",
	"bot_text" : "when your sleeping...",
	"style_info" : {
		"text-color" : [
			0,
			0,
			0
		],
		"text-size" : 24,
        "font" : "Ultra-Regular.ttf"
	},
	"file_id" : 5,
	"owner_id" : 2
}
```

We will discuss this a little more in class. However, most of the code is written for you, you simply need to 
refactor it. You don't need to connect this to our front end right now, you simply need to use "postman" or something similar to test your method is working. 

### Part 1 Deliverables

- In your assignments folder, create a folder called `meme_generator_pt1`
- Copy your version of `meme-api.py` into that folder.
- I should be able to run postman and hit your meme route to create a new "document" representing the meme.


### Part 2
Due: 10 Oct By Class time.

***Registration form***

Using the existing modal form, alter the registration portion of the form to allow for these text fields:

- first
- last
- email
- username
- password

The above data will need to be posted to our `/user/new` route. That route creates a document similar to the following in our mongo `users` database:

```json
{
	"_id" : 4,
	"username" : "theprez",
	"last" : "Bush",
	"password" : "8ea25a5ae7d0cffe511f17f133fe14cff2a0680748dac37e1c9b96e8",
	"email" : "gwbush@gmail.com",
	"first" : "George"
}
```
### Part 2 Deliverables

- In your assignments folder, create a folder called `meme_generator_pt2`
- Copy your `index.html` file into that folder.
- Copy your `meme-api.py` file into that folder (if you change the original).
- I should be able to replace my index file and my api script with yours to create a user. 

### Part 3
Due: 17 Oct by Class Time

User Login and session creation. 
More later.
