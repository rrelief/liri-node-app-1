
# LIRI Bot

## Commands:
npm start `<command>` where command is one of the following:

* movie-this + "movie title" 
* ex npm start movie-this 'sixteen candles'

##Overview
In this assignment, you will make LIRI, which is like iPhone's SIRI. However, while SIRI is a Speech Interpretation and Recognition Interface, LIRI is a Language Interpretation and Recognition Interface. LIRI will be a command line node app that takes in parameters and gives you back data.

####Before You Begin

* LIRI will display your latest tweets. As we do not want to display your personal account, or its keys, please make an alias account and add a few tweets to it!
* Make a new GitHub repository called liri-node-app and clone it to your computer.
* To retrieve the data that will power this app, you'll need to send requests to the Twitter, Spotify and OMDB APIs. You'll find these Node packages crucial for your assignment:

	* Twitter
	* Spotify
	* Request – you'll use Request to grab data from the OMDB API.
	* DotEnv
	
####Instructions
* Initialize a package.json file at your project root by running npm init.
* Make a .gitignore file and add the following lines to it. This will tell git not to track these files, and thus they won't be committed to Github.
	* node_modules
	* .DS_Store
	* .env
* Make a JavaScript file named keys.js.
	* Inside keys.js your file will look like this:
		`console.log('keys.js is loaded');`

		```
		exports.twitter = {
		  consumer_key: process.env.TWITTER_CONSUMER_KEY,
		  consumer_secret: process.env.TWITTER_CONSUMER_SECRET,
		  access_token_key: process.env.TWITTER_ACCESS_TOKEN_KEY,
		  access_token_secret: process.env.TWITTER_ACCESS_TOKEN_SECRET
		};
		
		exports.spotify = {
		  id: process.env.SPOTIFY_ID,
		  secret: process.env.SPOTIFY_SECRET
		};
		```
* Next, create a file named .env, add the following to it, replacing the values with your API keys (no quotes) once you have them:

	* **Spotify API keys**

		`SPOTIFY_ID=your-spotify-id`
		`SPOTIFY_SECRET=your-spotify-secret`

	* **Twitter API keys**

		```
		TWITTER_CONSUMER_KEY=your-twitter-consumer-key
		TWITTER_CONSUMER_SECRET=your-twitter-consumer-secret
		TWITTER_ACCESS_TOKEN_KEY=your-access-token-key
		TWITTER_ACCESS_TOKEN_SECRET=your-twitter-access-token-secret
		```
	•	This file will be used by the dotenv package to set what are known as environment variables to the global `process.env` object in node. These are values that are meant to be specific to the computer that node is running on, and since we are gitignoring this file, they won't be pushed to github — keeping our API key information private.

	* Get your Twitter API keys by following these steps:
		* Step One: Visit https://apps.twitter.com/app/new
		* Step Two: Fill out the form with dummy data. Type http://google.com in the Website input. Don't fill out the Callback URL input. Then submit the form.
		* Step Three: On the next screen, click the Keys and Access Tokens tab to get your consume key and secret.
		* Copy and paste them where the `<input here>` tags are inside your keys.js file.
		* Step Four: At the bottom of the page, click the **Create my access token button** to get your access token key and secret.
	* Copy the access token key and secret displayed at the bottom of the next screen. Paste them where the `<input here> `tags are inside your keys.js file.
	* Make a file called **random.txt**.
		* Inside of **random.txt** put the following in with no extra characters or white space: spotify-this-song,"I Want it That Way"
	* Make a JavaScript file named **liri.js**.
		* At the top of the liri.js file, add code to read and set any environment variables with the dotenv package:

			* `require("dotenv").config();`
			* Add code the code required to import the keys.js file and store it in a variable.
			* You should then be able to access your keys information like so
`var spotify = new Spotify(keys.spotify);`
`var client = new Twitter(keys.twitter);`

		* Make it so liri.js can take in one of the following commands:
			* my-tweets
			* spotify-this-song
			* movie-this
			* do-what-it-says

		* What Each Command Should Do
			* `node liri.js my-tweets` This will show your last 20 tweets and when they were created at in your terminal/bash window.
			* `node liri.js spotify-this-song '<song name here>'` This will show the following information about the song in your terminal/bash window
				* Artist(s)

				* The song's name

				* A preview link of the song from Spotify

				* The album that the song is from

				* If no song is provided then your program will default to "A Town Called Malice" by The Jam.
dfa
		* You will utilize the node-spotify-api package in order to retrieve song information from the Spotify API.

		* The Spotify API requires you sign up as a developer to generate the necessary credentials. You can follow these steps in order to generate a client id and client secret:

		* Step One: Visit https://developer.spotify.com/my-applications/#!/
		* Step Two: Either login to your existing Spotify account.
		* Step Three: Once logged in, navigate to https://developer.spotify.com/my-applications/#!/applications/create to register a new application to be used with the Spotify API. You can fill in whatever you'd like for these fields. When finished, click the "complete" button.
		* Step Four: On the next screen, scroll down to where you see your client id and client secret. Copy these values down somewhere, you'll need them to use the Spotify API and the node-spotify-api package.

		* `node liri.js movie-this '<movie name here>'` This will output the following information to your terminal/bash window:

  			* Title of the movie.
  			* Year the movie came out.
  			* IMDB Rating of the movie.
  			* Rotten Tomatoes Rating of the movie.
  			* Country where the movie was produced.
  			* Language of the movie.
  			* Plot of the movie.
  			* Actors in the movie.

  		* If the user doesn't type a movie in, the program will output data for the movie 'Mr. Nobody.'

  		* You'll use the request package to retrieve data from the OMDB API. Like all of the in-class activities, the OMDB API requires an API key. You may use trilogy. `http://www.omdbapi.com/?t=remember+the+titans&y=&plot=short&apikey=trilogy`
  		* `node liri.js do-what-it-says` Using the fs Node package, LIRI will take the text inside of random.txt and then use it to call one of LIRI's commands. It should run spotify-this-song for "I Want it That Way," as follows the text in random.txt.

  		* Feel free to change the text in that document to test out the feature for other commands.


### BONUS
  		* In addition to logging the data to your terminal/bash window, output the data to a .txt file called log.txt.
  		* Make sure you append each command you run to the log.txt file.
  		* Do not overwrite your file each time you run a command.

Minimum Requirements
Attempt to complete homework assignment as described in instructions. If unable to complete certain portions, please pseudocode these portions to describe what remains to be completed.


Create a README.md
Add a README.md to your repository describing the project. Here are some resources for creating your README.md. Here are some resources to help you along the way:
	•	About READMEs

	•	Mastering Markdown



Add To Your Portfolio
After completing the homework please add the piece to your portfolio. Make sure to add a link to your updated portfolio in the comments section of your homework so the TAs can easily ensure you completed this step when they are grading the assignment. To receive an 'A' on any assignment, you must link to it from your portfolio. 


