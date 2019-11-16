# S18 | Module Introdution
---
Authentication Logic
`file`
<img src="./assets/section-18/0.png" alt="smile" width="800" />
 - this authentication is for single page. Where we dont have to authenticate a user for every page like in traditional apps. 
 - In SPAS we only deal with a single file coming from the server i.e index.html
 - In Traditional multi page app we have multiple pages coming from server where we have to maintain authentication using session and cookies.

 # S18 | Understanding Authentication in Single Page Applications
---
How it works 
`file`
<img src="./assets/section-18/1.png" alt="smile" width="800" />
- The SPA running on the browser will send the Auth data i.e email/password of the user.
- The server will validate the Auth data and send back a token (instead of a session as in a traditional app).
- This token can then be stored in the browser in the localStorage so that the token persists on page reload. 
- When we need to access protected resource like changing password or creating a blog post we will send this token along with the request. The server can validates the token. Unlike MPAs where a server maintains a session and can cross check the Auth data on every request.
- Note that only  tokens gererated by the server and sent to the client will be valid. 
- THe server here is a RESTful APIs server

 # S18 | Required App Adjustments
---
## Required adjustments
`file`
<img src="./assets/section-18/3.png" alt="smile" width="800" /> 

## Auth.js - Creating a signup and signin view
Creating a new component as container  
`Auth.js`
<img src="./assets/section-18/4.png" alt="smile" width="800" /> 

Add form controls
`Auth.js`
<img src="./assets/section-18/4.1.png" alt="smile" width="800" />

Control - Email
`Auth.js`
<img src="./assets/section-18/4.3.png" alt="smile" width="800" /> 

Control - Password
`Auth.js`
<img src="./assets/section-18/4.4.png" alt="smile" width="800" /> 

Import the UI Input and Button custom components
`Auth.js`
<img src="./assets/section-18/5.png" alt="smile" width="800" /> 

Render() - loop through the form controls 
`Auth.js`
<img src="./assets/section-18/5.7.png" alt="smile" width="800" /> 

Creating a new component as container  
`Auth.js`
<img src="./assets/section-18/5..png" alt="smile" width="800" /> 

Render() - form and the button
`Auth.js`
<img src="./assets/section-18/5.3.png" alt="smile" width="800" /> 

## App.js - Setup the Route
Current setup
`App.js`
<img src="./assets/section-18/6.png" alt="smile" width="800" /> 

Add the Auth Route
`App.js`
<img src="./assets/section-18/6.1.png" alt="smile" width="800" /> 

## NavigationItems.js - Add new nav
Add Authenticate to Navigation - so that we can reach the Auth route
`NavigationItems.js`
<img src="./assets/section-18/7.png" alt="smile" width="800" /> 

## Output 
Cannot see the inputs
`file`
<img src="./assets/section-18/8.1.png" alt="smile" width="800" /> 

## Auth.css - Styling 
Lets add some stying to the form
`Auth.css`
<img src="./assets/section-18/9.1.png" alt="smile" width="800" /> 

Import css
`Auth.js`
<img src="./assets/section-18/9.2.png" alt="smile" width="800" /> 

Add to the Jsx div
`Auth.js`
<img src="./assets/section-18/9.3.png" alt="smile" width="800" /> 


## Form Validation
Add the method for validation
`Auth.js`
<img src="./assets/section-18/10.png" alt="smile" width="800" /> 
- copied from contactData

Continued
`Auth.js`
<img src="./assets/section-18/10.1.png" alt="smile" width="800" /> 

input Change Hadler
`Auth.js`
<img src="./assets/section-18/10.2.png" alt="smile" width="800" /> 

Cont..
`Auth.js`
<img src="./assets/section-18/10.3.png" alt="smile" width="800" /> 

Update the state after validation of each control
`Auth.js`
<img src="./assets/section-18/10.5.png" alt="smile" width="800" /> 

Connect the event handler
`Auth.js`
<img src="./assets/section-18/10.6.png" alt="smile" width="800" /> 
- see the `changed` prop

## Output - Validation
Validation working
`file`
<img src="./assets/section-18/11.png" alt="smile" width="800" /> 
- see the red password field

# S18 | Adding Actions
---
We want the submit button in the Authenticate page to work
`file`
<img src="./assets/section-18/12.png" alt="smile" width="800" />
- We will create action creators 

## auth.js - Actions - Creating Action creators
Create `auth.js` in the actions folder 
`actions/auth.js`
<img src="./assets/section-18/12.1.png" alt="smile" width="800" /> 
- this will hold the authentication related actions

Create actionTypes
`actions/actionTypes.js`
<img src="./assets/section-18/12.2.png" alt="smile" width="800" /> 
- AUTH_START, AUTH_SUCCESS, AUTH_FAIL 


`authStart` - action creator
`actions/auth.js`
<img src="./assets/section-18/12.3.png" alt="smile" width="800" /> 
- this action creator will be used to set a loading state and show a spinner
- there is no payload

`authSuccess` - action creator
`actions/auth.js`
<img src="./assets/section-18/12.4.png" alt="smile" width="800" /> 
- payload passed is authData - we will see this later in details

`authFail` - action creator
`actions/auth.js`
<img src="./assets/section-18/12.5.png" alt="smile" width="800" /> 

`auth` - action creator
`actions/auth.js`
<img src="./assets/section-18/12.6.png" alt="smile" width="800" /> 
- this holds the async code doing the authentication
- we expect the email and password
- we get the dispatch as an argument in this function - due to `REDUX THUNK`
- in there we want to authenticate the user
 
`auth` - action creator
`actions/auth.js`
<img src="./assets/section-18/12.7.png" alt="smile" width="800" /> 
- we will dispatch authStart to at least set this state 

## Auth.js - Container - Connect actions to container so that we can dispatch them 
 Import my actions 
`actions/index.js`
<img src="./assets/section-18/13.0.png" alt="smile" width="800" /> 
 - add the auth action creators to the index.js file where we bundle all the exports from the actions folder

 Import my actions 
`containers/auth.js`
<img src="./assets/section-18/13.1.png" alt="smile" width="800" /> 

mapDispatchToProps - configure this so that we can use props to dispatch actions
`containers/auth.js`
<img src="./assets/section-18/13.2.png" alt="smile" width="800" /> 

Cont.. 
`containers/auth.js`
<img src="./assets/section-18/13.3.png" alt="smile" width="800" /> 
- dispatch the `auth()` action
- pass on the email and password to the actions

mapDispatchToProps only makes sense if we **connect** to this container
import `connect` from react-redux
`containers/auth.js`
<img src="./assets/section-18/13.4.png" alt="smile" width="800" />  

execute `Connect`
`containers/auth.js`
<img src="./assets/section-18/13.5.png" alt="smile" width="800" /> 
- 1st arg : null - `mapStateToProps` is null
- 2nd arg : mapDispatchToProps
- Now we can execute `onAuth()` on our props in this container
- We want to do this when the form is submitted

Add Form Submit Handler
`containers/auth.js`
<img src="./assets/section-18/14.png" alt="smile" width="800" /> 

Add the method to the container
`containers/auth.js`
<img src="./assets/section-18/14.1.png" alt="smile" width="800" /> 
- we expect to get the event as 1st arg
- we need to pass the email and password
- we get email/pass from the state

Get email/pass
`containers/auth.js`
<img src="./assets/section-18/14.2.png" alt="smile" width="800" /> 
- this.state.controls.email.value
- this.state.controls.password.value

## Output
Click submit
<img src="./assets/section-18/15.png" alt="smile" width="800" /> 

AUTH_START action was dispatched 
``
<img src="./assets/section-18/15.1.png" alt="smile" width="800" /> 
- but of course nothing else works
- we will do the async call and authenticate using firebase


# S18 | Getting a Token from the Backend
---
What you will not get in this course
- how to validate email on the server 
- how to create that token
- this is not covered here

Firebase - Authentication - Signin method
`file`
<img src="./assets/section-18/16.png" alt="smile" width="800" /> 

Enable email 
`file`
<img src="./assets/section-18/16.1.png" alt="smile" width="800" /> 
- now we reach certain REST API end points to sign up user and get a token

To find out which address we need to send that 
- Google firebase rest auth
`flle`
<img src="./assets/section-18/16.2.png" alt="smile" width="800" /> 
- the 2nd result

Find the endpoint to sign up new users 
`file`
<img src="./assets/section-18/16.3.png" alt="smile" width="800" /> 
- copy the endpoint and send the request

We will use the default axios instance 
- Import axios
`actions/auth.js`
<img src="./assets/section-18/17.0.png" alt="smile" width="800" /> 
- then i can start sending requests

Send request to the endpoint 
`actions/auth.js`
<img src="./assets/section-18/17.1.png" alt="smile" width="800" /> 
<img src="./assets/section-18/17.2.png" alt="smile" width="800" /> 
 - `API KEY` portion - replace with our project api key

Firebase - Authentication - Web Setup
`actions/auth.js`
<img src="./assets/section-18/17.3.png" alt="smile" width="800" /> 
- copy the API KEY for our project without quotes
- replace within the firebase endpoint for user sign up
- this identifies our application

Send the expected data to the endpoint
``
<img src="./assets/section-18/17.4.png" alt="smile" width="800" /> 

construct authData
`actions/auth.js`
<img src="./assets/section-18/17.5.png" alt="smile" width="800" /> 

Attach this data to the post request
<img src="./assets/section-18/17.6.png" alt="smile" width="800" /> 

Send response.data to authSuccess on success 
Send err to authFail on failure
<img src="./assets/section-18/17.7.png" alt="smile" width="800" /> 

## Output 
Submit 
`file`
<img src="./assets/section-18/18.png" alt="smile" width="800" /> 

Redux 
`file`
<img src="./assets/section-18/18.1.png" alt="smile" width="800" /> 
- We see AUTH_START and AUTH_SUCCESS

See console to see the response data we get back
`file`
<img src="./assets/section-18/18.2.png" alt="smile" width="800" /> 
- shows that idToken is valid for 3600 sec - 1hour 
- the refreshToken can be use to get a new idToken

Firebase - output - user created with userID
`file`
<img src="./assets/section-18/18.3.png" alt="smile" width="800" /> 

If invalid form data is sent - we get an error
<img src="./assets/section-18/18.4.png" alt="smile" width="800" />
<img src="./assets/section-18/18.5.png" alt="smile" width="800" /> 

For subsequent requests we will use the idToken and the refreshToken and the expiresIn info.

# S18 | Adding Sign-In
## Container - Auth.js
Adding a sign in button
`containers/auth.js`
<img src="./assets/section-18/19.png" alt="smile" width="800" /> 
<img src="./assets/section-18/19.1.png" alt="smile" width="800" /> 

isSignup - state property
`containers/auth.js`
<img src="./assets/section-18/19.2.png" alt="smile" width="800" /> 
- this property should be true initially

Switch the isSignup to false when submit button is clicked
`containers/auth.js`
<img src="./assets/section-18/19.3.png" alt="smile" width="800" /> 

Render() - Button
`containers/auth.js`
<img src="./assets/section-18/19.4.png" alt="smile" width="800" /> 
<img src="./assets/section-18/19.5.png" alt="smile" width="800" /> 

Recall - Button.js
`components/Button.js`
<img src="./assets/section-18/19.6.png" alt="smile" width="800" /> 

`clicked` - defined
`containers/auth.js`
<img src="./assets/section-18/19.7.png" alt="smile" width="800" /> 

## Actions - Auth.js
To make it really functional we need to something in the `submitHandler`
We always call onAuth where we always execute the `auth` action 
`actions/auth.js`
<img src="./assets/section-18/20.png" alt="smile" width="800" /> 

We want to get a third argument in the action - signup or signin
`actions/auth.js`
<img src="./assets/section-18/20.2.png" alt="smile" width="800" /> 

signin url 
<img src="./assets/section-18/20.4.png" alt="smile" width="800" /> 

We will send the request to different urls for different methods  
`actions/auth.js`
<img src="./assets/section-18/20.5.png" alt="smile" width="800" />  
<img src="./assets/section-18/20.6.png" alt="smile" width="800" />  
- send the post req to the `url` 

## Container - Auth.js
Pass the isSignup argument to the action creator from the container
`containers/auth.js`
<img src="./assets/section-18/21.png" alt="smile" width="800" />  
<img src="./assets/section-18/21.1.png" alt="smile" width="800" />  
<img src="./assets/section-18/21.2.png" alt="smile" width="800" />  

Pass the isSignup from the submitHandler
`containers/auth.js`
<img src="./assets/section-18/21.3.png" alt="smile" width="800" /> 
<img src="./assets/section-18/21.4.png" alt="smile" width="800" />  

## Output
When trying to sign up with same email 
<img src="./assets/section-18/22.png" alt="smile" width="800" />  
- AUTH_FAIL
- EMAIL EXISTS

When signing in as existing user r
<img src="./assets/section-18/22.1.png" alt="smile" width="800" />  
- AUTH_SUCCESS
- We get back the token 
- next challenge is to store the token so that we can use it in the future

# S18 | Storing the Token
---
## Reducer - Auth.js
Create a new reducer - auth.js
`reducers/auth.js`
<img src="./assets/section-18/23.png" alt="smile" width="800" /> 
- we will handle the auth actions and auth state here 

initialState and reducer function 
`reducers/auth.js`
<img src="./assets/section-18/23.1.png" alt="smile" width="800" /> 

Import the updateObject from utility file 
`reducers/auth.js`
<img src="./assets/section-18/23.2.png" alt="smile" width="800" /> 

use updateOBject to update the state
`reducers/auth.js`
<img src="./assets/section-18/23.3.png" alt="smile" width="800" /> 
- set the error to null and loading to true for `AUTH_START` action type

Return the state for default case 
`reducers/auth.js`
<img src="./assets/section-18/23.4.png" alt="smile" width="800" /> 

Make the reducer leaner and thinner in code
`reducers/auth.js`
<img src="./assets/section-18/23.5.png" alt="smile" width="800" /> 
- define authStart function which takes the state and action and returns the new state.

`authSuccess` - return the state for AUTH_SUCCESS
`reducers/auth.js`
<img src="./assets/section-18/23.6.png" alt="smile" width="800" /> 
- set the token and userid from the action payload
- set error as null 
- set loading as false - since we are done loading

`authFail` - return state for AUTH_FAIL
`reducers/auth.js`
<img src="./assets/section-18/23.7.png" alt="smile" width="800" /> 

Use the functions in the reducer case statements
`reducers/auth.js`
<img src="./assets/section-18/23.9.png" alt="smile" width="800" /> 

## Combine the reducer - Index.js
Now we want to combine this reducer with other reducers
`index.js`
<img src="./assets/section-18/24.png" alt="smile" width="800" /> 
- import the auth reducer first 
- auth property holds the auth reducer
- combineReducers combines all the reducers

## Note
We are not passing the idToken or the userId when we dispatch the actions 
`actions/auth.js`
<img src="./assets/section-18/25.png" alt="smile" width="800" /> 

Lets inspect the response we get when we sign in
<img src="./assets/section-18/26.png" alt="smile" width="800" /> 
<img src="./assets/section-18/26.1.png" alt="smile" width="800" /> 
- idToken is the token 
- localId is the userID

## Action - Auth.js
Current Code
`actions/auth.js`
<img src="./assets/section-18/27.png" alt="smile" width="800" /> 

authSuccess method now expects token and userId as args
`actions/auth.js`
<img src="./assets/section-18/28.0.png" alt="smile" width="800" /> 
- set these as the payloads for the action sent to the reducer
- type, token , userId
- we try to extract these payload info in the reducer as idToken and userId
  `reducers/auth.js` 
  <img src="./assets/section-18/28.1.png" alt="smile" width="800" /> 

Pass on the token and userId where the action is dispatched
CUrrent Code
`actions/auth.js`
<img src="./assets/section-18/29.png" alt="smile" width="800" /> 

Pass the idToken and localId
`actions/auth.js`
<img src="./assets/section-18/29.1.png" alt="smile" width="800" /> 

## Output
On Submit while in SIGN-IN mode , we retreive the token and userId
<img src="./assets/section-18/30.png" alt="smile" width="800" /> 
- we are thus storing the authentication status
- but we are not yet showing a spinner while authenticating in progress

# S18 | Adding a Spinner
--- 
Adding a spinner while authentication is in progress.

## Spinner while Authentication
#### Container - Auth.js
Import the Spinner Component
`containers/auth.js`
<img src="./assets/section-18/31.png" alt="smile" width="800" /> 

Now I want to display the spinner as long as we are loading and for that,
- I need to know if we're loading and we're storing that information in our auth state, for that
- I need to get a piece of that state in my auth container
- This is a case for const mapStateToProps, 
- There we get the state and can now map a slice of it to our local props.
  
`containers/auth.js`
<img src="./assets/section-18/32.png" alt="smile" width="800" /> 
- We get the state and can now map a slice of it to our local props 'loading'

Pass mapStateToProps to our connect function
`containers/auth.js`
<img src="./assets/section-18/33.png" alt="smile" width="800" /> 

In render method we can render a Spinner
`containers/auth.js`
<img src="./assets/section-18/34.png" alt="smile" width="800" /> 
- That should be all

## Show Error If Wrong Data Submitted
#### Container - Auth.js
Map the error from the auth slice to local error prop
`containers/auth.js`
<img src="./assets/section-18/35.png" alt="smile" width="800" /> 

Display an error message 
`containers/auth.js`
<img src="./assets/section-18/36.png" alt="smile" width="800" />

Output the error message above the form
`containers/auth.js`
<img src="./assets/section-18/37.png" alt="smile" width="800" />  

#### Actions - Auth.js
Before we see something we have to ensure that we store that error
`actions/auth.js`
<img src="./assets/section-18/38.png" alt="smile" width="800" /> 

## Output
Invalid email
<img src="./assets/section-18/39.png" alt="smile" width="800" /> 

Email exists
<img src="./assets/section-18/40.png" alt="smile" width="800" /> 