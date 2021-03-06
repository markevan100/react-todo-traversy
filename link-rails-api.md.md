---


---

<p>Hey Sav,</p>
<p>Looking for a little direction if you have a minute at some point. My task today: link a React site to a Rails (API only) backend. In this case, the React site is already created, it is a simple Todo app. The Rails API has not yet been created. I added you as a collaborator to the React app on Github this morning.</p>
<p>Here is what I think this process will look like:</p>
<ol>
<li>
<p>Generate a new Rails API using the command:<br>
<code>rails new reacttodo --api --no-sprockets -d postgresql</code><br>
The <code>--api</code> tag will get rid of front-end stuff from the build, the <code>--no-sprockets</code> will get rid of the asset pipeline, and the last flag will set postgeSQL as the default db for easy production.</p>
</li>
<li>
<p>Create my todos in my Rails app using the command:<br>
<code>rails g scaffold Todo title:string complete:boolean</code><br>
Granted, I shouldn’t really be using scaffold, but this is an exercise in connecting to React, not building things in Rails, so let’s make it easy. The only attributes my todos have are the title and the completed. I eventually want my boolean to default to false, but I’m not exactly sure how to do that in the original generate. Just <code>default: false</code> at the end? I can also just add a migration change later and put it in, I know how to do that.</p>
</li>
</ol>
<ol start="3">
<li>Now it’s time for some linkage!<br>
I’ve been trying to figure this our all … day. Can’t find something easy to show me how to do it. Basically, if you look at <a href="https://github.com/markevan100/react-todo-traversy/blob/master/src/App.js">this page</a> you’ll see that I have three functions that need to link to my db, my index, my add, and my delete. In there, with the axios (do I need that?) it looks like I just have to provide the url. All the examples I’ve found show this with some local port, which I have to assume is just for development. For deploy, do I simply deploy my backend (through Heroku is my plan) get the url for that route and then plug it in here? How do they connnnnnnneeeccct?</li>
</ol>

#2 for the migration default, I don't think default migration generator supports defaults yet, so you'll just have to add it either manually in the migration file or in the command like using something like 
<code>add_column :todo, :completed, :bool,  :default => 0</code>
key words 'something like'

#3. So you need axios (or other API fetcher.. things), but I like axios. This is 'the connector'. So what I did was have my API set up so that it runs on localhost:3001, while that is running, axios can then go visit your API to collect that data and then bring it back to your localhost:3000 port where your react app is running. 
Not going to lie, it was hell getting in up and running on Heroku, but it's doable. But, I've only done it going from just running locally to then deploying on Heroku instead of doing it from Heroku from the start, so that could be easier. 

What sort of errors are you getting, or have you been able to get as far as being able to get errors?





