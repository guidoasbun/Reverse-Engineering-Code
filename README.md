# Unit 14 Sequelize Homework: Reverse Engineering Code
## File Structure
## 1.  config
## middleware
### - isAuthenticaticated.js
•	checks if the user is already authenticated
### - config.json
•	contains 3 json objects that define the database configuration
### - passport.js
•	requires passport npm package
•	it uses LocalStrategy for email password authentication
•	users will use email and password to sign in
•	if there is no email in the DB, “incorrect email” is the message
•	if incorrect password, “incorrect password” is the message
•	if it passes authentication, the user object is returned
## 2. models
### - index.js
•	sets up database with sequelized
### - user.js
•	requires bcrypt for password hashing
•	creates the user model
•	email – string type, can not be null, must be unique, must be email format
•	password – string type, cannot be null
•	validPassword function – validates password
•	add.Hook function – runs user creation, and hashes out password
## 3.  public
## js
### - login.js
•	uses jQuery
•	ready function - initializes variables from the DOM inputs, loginForm, emailInput, passwordInput. Validates input of a email and password. If true, calls the loginUser function
•	loginUser function – makes axios request to verifies email and password
### - members.js
•	ready function – sets up text of an html element with email of user
### - signup.js
•	ready function – like login.js
•	signUpUser – creates a new user
## stylesheets
### - login.html
•	main page for the application
•	login form
•	input for email and password
•	login button
•	or link to sign up
### - members.html
•	page displays after users successfully log in
### - signup.html
•	sign up page
•	input for email and password
•	link to login
## 4. routes
### - api-routes.js
•	it has 2 post routes
•	/api/login – if the user verified password and email, the are directed to this route
•	/api/signup – route to sign up the user, takes in the email and password and posts it to the DB
•	2 get routes
•	/api/logout – logs out user and redirects to the main screen
•	/api/user_data – if the user is not logged in, it will return an empty json, otherwire, it will send back the user email and id
### - html-routes.js
•	checks if the user is logged in using middleware
•	has 3 get routes
•	/ - if user has an account, it redirects to the members page
•	/login – after user logs in, redirect to members page
•	/members – if user is not logged in and tries to access route, they will be redirected to signup page
## 5.  server.js
•	Server file that puts everything together. 
•	Requires all the NPM packages
•	Sets up the ports
•	Sets up middleware an express app
•	Uses sessions to keep track of login status
•	Pull sin all the routes
•	Syncs database
