---
layout: post
title: Deploying a React App with Heroku
---

This was a very practical problem that I recently faced. I had used Heroku before, and I had used Create-React-App to bootstrap a React project. But when it came time to deploy the React project, I faced a few hurdles. By the way, I'm using a Windows 10 laptop here. My goal is to share a really quick way Heroku can help you deploy this type of project, so that you can share your work with the world. 

*** Please be sure to type in all commands instead of copy and pasting to ensure ultimate accuracy ***

PREREQUISITES

Download and install Git Bash.

Git Bash download link: [https://git-scm.com/download/win](https://git-scm.com/download/win)

Download and install Node/NPM.

NodeJS download link: [https://nodejs.org/en/](https://nodejs.org/en/)

Download and install Heroku CLI. 

Heroku CLI download link: [https://devcenter.heroku.com/articles/heroku-cli](https://devcenter.heroku.com/articles/heroku-cli)

Restart your PC after these downloads to ensure changes go through. 

1) Heroku is a provider of free hosting. This is a huge advantage to developers who seek to share their work as it progresses. Sign up [here](https://signup.heroku.com/) and then confirm your account by heading over to your email inbox.

2) Set up your Create-React-App

This will bootstrap your React app and make it quick and easy to get started. For more info, head on over to the [CRA GitHub](https://github.com/facebook/create-react-app)

	npx create-react-app my-app
	cd my-app
	npm start

3) Edit your package.json file. 

We'll be adding a new object referred to as engines. Inside of this object, we need to specify our npm and node versions. Once you're done adding this object, save your file. 

	"engines": {
    "npm": "3.10.9",
    "node": "6.9.2"
	},

4) Create Your Heroku Git Repo

Creating this repository will allow us to finally deploy the app! If you're not already there, in Git Bash, navigate to the root of your React app folder. To make sure your Heroku CLI is installed and can be used, type out the 'heroku --version' command. Now we can set up the repository by using the following commands one-by-one. 

	heroku login (enter heroku credentials)
	git init
	git add .
	git commit -m "commit message"
	heroku create (two links will generate, copy the second one)
	git remote add heroku PASTE LINK HERE
	git remote -v (verify heroku remote present)
	git push origin master
	git push heroku master
	heroku open 


*** A little problem here that directly impacted my experience. If Heroku commands stall out, this can likely be due to an autoupdating function of the CLI, and you can follow these steps to hopefully ensure success. This issue has been well documented [here](https://github.com/heroku/cli/issues/623).

	Go to the Heroku AppData directory (%LOCALAPPDATA%\heroku in Windows).
	Look for the autoupdate and autoupdate.log files. If they're not there, try running a Heroku command in the CLI.
	Delete both these files.
	In the command prompt, run heroku update.
	See if the issue is fixed by running another heroku command.

	Finally, if this doesn't work, try running steps in another Git Bash command prompt. 

Enjoy this awesome tool and let me know if you have any questions!


