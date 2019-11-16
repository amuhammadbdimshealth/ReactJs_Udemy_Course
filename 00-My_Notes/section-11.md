# S11 | Routing
## Objective 
1. We will go through the section without coding - to save time
2. We will take snapshots as we see the lectures
3. We will code in the Burger Builder Project

## S11 | Routing and SPAs
---
<img src="./assets/section-11/1.png" alt="smile" width="800" />

## S11 | Setting up Links
---
### Objective
1. Setup links for different pages in the demo-post application below:

#### Lecture Snapshots
<img src="./assets/section-11/2.png" alt="smile" width="800" />
<img src="./assets/section-11/3.png" alt="smile" width="800" />
<img src="./assets/section-11/4.png" alt="smile" width="800" />
<img src="./assets/section-11/5.png" alt="smile" width="800" />
<img src="./assets/section-11/6.png" alt="smile" width="800" />

## S11 | Setting up the Router Package
---
### Lecture Snapshots

We will use routing in the blog component
<img src="./assets/section-11/7.png" alt="smile" width="800" /> 
<img src="./assets/section-11/8.png" alt="smile" width="800" />   
<img src="./assets/section-11/9.png" alt="smile" width="800" /> 

Enable Routing
<img src="./assets/section-11/10.png" alt="smile" width="800" /> 

This is the Router now.
<img src="./assets/section-11/11.png" alt="smile" width="800" /> 

We will use routing in the blog component
<img src="./assets/section-11/13.png" alt="smile" width="800" /> 

## S11 | Preparing the Project for Routing
---
<img src="./assets/section-11/14.png" alt="smile" width="800" />
<img src="./assets/section-11/15.png" alt="smile" width="800" />
<img src="./assets/section-11/16.png" alt="smile" width="800" />
<img src="./assets/section-11/17.png" alt="smile" width="800" />
<img src="./assets/section-11/18.png" alt="smile" width="800" />
<img src="./assets/section-11/19.png" alt="smile" width="800" />
<img src="./assets/section-11/20.png" alt="smile" width="800" />
<img src="./assets/section-11/21.png" alt="smile" width="800" />
<img src="./assets/section-11/22.png" alt="smile" width="800" />

## S11 | Setting Up and Rendering Routes
---
### Lecture snapshots
<img src="./assets/section-11/23.png" alt="smile" width="800" />
<img src="./assets/section-11/24.png" alt="smile" width="800" />
<img src="./assets/section-11/25.png" alt="smile" width="800" />
<img src="./assets/section-11/26.png" alt="smile" width="800" />
<img src="./assets/section-11/27.png" alt="smile" width="800" />

The React Router to determine which path you are on, sees if you current path starts with this path, so if this is a **prefix**. You can override this behaviour using `exact` to match exactly the **whole path string**.
<img src="./assets/section-11/28.png" alt="smile" width="800" />

Multiple Routes for same path ? 
<img src="./assets/section-11/29.png" alt="smile" width="800" />

Output
<img src="./assets/section-11/30.png" alt="smile" width="800" />

## S11 | Rendering Components For Routes
---
Comment out
<img src="./assets/section-11/31.png" alt="smile" width="800" />

Using Component property
<img src="./assets/section-11/32.png" alt="smile" width="800" />
<img src="./assets/section-11/33.png" alt="smile" width="800" />

## S11 | Switching Between Pages
---
### Lecture snapshots 
<img src="./assets/section-11/34.png" alt="smile" width="800" />
<img src="./assets/section-11/35.png" alt="smile" width="800" />
<img src="./assets/section-11/36.png" alt="smile" width="800" />
<img src="./assets/section-11/37.png" alt="smile" width="800" />

### Issue
1. But our application reloads each time we click the links
2. This causes the aplication state to be lost
3. We want to avoid this state loss and let react load only the Route component while staying on the single page without reloading.

## S11 | Using Links To Switch Pages
---
### Objective 
1. We want to stay inside of the application when clicking links inside of it.

### Lecture snapshots
<img src="./assets/section-11/38.png" alt="smile" width="800" />
<img src="./assets/section-11/39.png" alt="smile" width="800" />
<img src="./assets/section-11/40.png" alt="smile" width="800" />
This lets react render only parts of the DOM Depending on the Route path and not re-load the entire application while navigating.

## S11 | Using Routing-Related Props
---
### Objective
1. Get Introduced to the default props passed by the React Router
2. We can use these props to extract query params, move to a hash fragment, etc.
   
### Lecture snapshots
Lets see the props in the `Posts` Component
<img src="./assets/section-11/41.png" alt="smile" width="800" />

These porps were passed by React Router automatically. 
<img src="./assets/section-11/42.png" alt="smile" width="800" />
<img src="./assets/section-11/43.png" alt="smile" width="800" />
<img src="./assets/section-11/44.png" alt="smile" width="800" />
<img src="./assets/section-11/45.png" alt="smile" width="800" />


Lets see the props in the `NewPost` Component
<img src="./assets/section-11/46.png" alt="smile" width="800" />
<img src="./assets/section-11/47.png" alt="smile" width="800" />
<img src="./assets/section-11/48.png" alt="smile" width="800" />

Later we will see how we can use the histroy object to use a method it provides us.

## S11 | The `withRouter` HOC & Route Props
---
### Objective
1. Find out what gets passed as props of a Component which gets loaded as part of another component. Like `Post` gets loaded as a part of `Posts` which gets loaded in the `Blog`component as a `Route`.

### Lecture snapshots
Lets see the props in the `Post` Component
<img src="./assets/section-11/49.png" alt="smile" width="800" />

We dont see the default props passed by React Router
<img src="./assets/section-11/50.png" alt="smile" width="800" />

But we see it in the `Posts` Component which gets loaded as a Route in the `Blog` component
<img src="./assets/section-11/51.png" alt="smile" width="800" />

So the Routing related props are not passed the component tree.
But there are two ways to get access to the Route props from inside a component rendered from a Route Component..

We can get access to the props passed by React Router in a Child (`Post`) Component in 2 ways : 
1. We can just pass them on using the spread operator
<img src="./assets/section-11/52.png" alt="smile" width="800" />

2. Using a Higher Order Component on the `Post` (child) Component
<img src="./assets/section-11/53.png" alt="smile" width="800" />
The withRouter hoc can be used to wrap any component where you expect to get the Router props from the nearest loaded Route
<img src="./assets/section-11/54.png" alt="smile" width="800" />
<img src="./assets/section-11/55.png" alt="smile" width="800" />

## S11 | Absolute Vs Relative Paths
---
### Objective
 
### Lecture snapshots
* **Absolute path** - The `newpost` will always be appended to the root domain `example.com`. So the path will be `example.com/new-post`. 

* Even if initially you were in a route with url `example.com/posts` this will not turn into a **Relative Path** i.e `example.com/posts/new-post` (appending to the end of the current path)

  <img src="./assets/section-11/56.png" alt="smile" width="800" />

* **Relative Path** - What if you wanted to append at the end of your current path ?
  * You have to build the path **dynamically** by taking into advantage the fact that that you know your **current path**

  <img src="./assets/section-11/57.png" alt="smile" width="800" />
  <img src="./assets/section-11/58.png" alt="smile" width="800" />
  <img src="./assets/section-11/59.png" alt="smile" width="800" />
  <img src="./assets/section-11/60.png" alt="smile" width="800" />


## S11 | Styling The Active Route 
---
### Objective
1. Add custom css to the active React Links
2. This does not happen automatically. 

### How ?
1. We have to manually tell React Router that we want to apply custom css on the anchor tags it creates.
2. We need to use `NavLink` component instead of the `Link` component to attach a class when the link is active

### Lecture snapshots
Before
<img src="./assets/section-11/61.png" alt="smile" width="800" />
Import `NavLink`
<img src="./assets/section-11/62.png" alt="smile" width="800" />
Use NavLink, not Link
<img src="./assets/section-11/63.png" alt="smile" width="800" />
**active** class is attached now. This css class was not present before when using `Link` component
<img src="./assets/section-11/64.png" alt="smile" width="800" />
Now we can apply some styling
<img src="./assets/section-11/65.png" alt="smile" width="800" />
But now both link Home and NewPost are orange. But if we click on Home, only Home is orange. Why is that?
<img src="./assets/section-11/66.png" alt="smile" width="800" /> 
Because by default React Router treats these paths as prefixes.
<img src="./assets/section-11/67.png" alt="smile" width="800" />
Same is true for links. When checking whether a link is active or not it treats this as a prefix.
<img src="./assets/section-11/68.png" alt="smile" width="800" /> 
We have to add exact to let React Router know that the full path should be this, for this to be the active link.
Its needed only for the 1st link not the 2nd since there is no nesting for that.
<img src="./assets/section-11/69.png" alt="smile" width="800" /> 
Sometime you might not want `active` to be the active className. 
<img src="./assets/section-11/70.png" alt="smile" width="800" /> 
You can override the class that should be appended. Use the prop `activeClassName`.
<img src="./assets/section-11/71.png" alt="smile" width="800" /> 
<img src="./assets/section-11/72.png" alt="smile" width="800" /> 
activeStyle
<img src="./assets/section-11/73.png" alt="smile" width="800" /> 

## S11 | Passing Route Parameters
---
### Objective
1. Click on a single post and load that.
2. Pass the postid on click and load the appropriate post

### Lecture Snapshots

Passing the postID on click
<img src="./assets/section-11/74.png" alt="smile" width="800" /> 

We cannot have something like this `/1`, `/2` as different Routes for different posts since we dont know how many possible values are there.
<img src="./assets/section-11/75.png" alt="smile" width="800" /> 

We need to setup the route dynamically since each post has different postID. We will use the syntax `/:id` as a dynamic/flexible Route which says to the React Router that we have something dynamic, **a route parameter**, after the `/` 
<img src="./assets/section-11/76.png" alt="smile" width="800" /> 

We need to pass the paramter when clicking on a Route. **2 ways to do that** : 

1. **Wrap the `Post` component with a `Link` component and have the `to` prop refer to a dynamic route url.**

    <img src="./assets/section-11/77.png" alt="smile" width="800" /> 
    <img src="./assets/section-11/78.png" alt="smile" width="800" /> 

    Now we need to make sure that we load the `FullPost` component when going to this Route below:
    <img src="./assets/section-11/79.png" alt="smile" width="800" /> 
    <img src="./assets/section-11/81.png" alt="smile" width="800" />  
    <img src="./assets/section-11/82.png" alt="smile" width="800" /> 
    
    Error
    <img src="./assets/section-11/83.png" alt="smile" width="800" /> 
    <img src="./assets/section-11/84.png" alt="smile" width="800" /> 

    When you click a post, there is ID in the url like `http://localhost:3000/1`.
    <img src="./assets/section-11/85.png" alt="smile" width="800" /> 

    But we see "Please select a Post" and not the relevant Post because the `this.prop.id` in the `FullPost` component is not set anymore. We are not retrieving the postID parameter set in the Route `/1`,`/2`.
    <img src="./assets/section-11/86.png" alt="smile" width="800" /> 

    Whats working so far is : 
      1. We can click different post and load urls with different IDs
      2. We are also loading the FullPost component
      3. **But we now have to extract the Route paramter from the url to load the correct FullPost.**
      <img src="./assets/section-11/87.png" alt="smile" width="800" />

## S11 | Extracting Route Parameters
---
### Objective
1. Extract the Route parameters

### Lecture Snapshots
Till now, we have set up the link and we set the `to` property where we passed the `postID`
<img src="./assets/section-11/88.png" alt="smile" width="800" />

We are able to recieve the postID since we have set up a flexible path here.
<img src="./assets/section-11/89.png" alt="smile" width="800" />

Now we need to retrieve that parameter too. In the `FullPost` component the this.props.id does not work as expected.
<img src="./assets/section-11/93.png" alt="smile" width="800" />

Lets check the `props` object passed to the FullPost component when clicking a `Post`. Note the `params.id = 3`
<img src="./assets/section-11/91.png" alt="smile" width="800" />

Its called `id` because that is the name we set up here.
<img src="./assets/section-11/92.png" alt="smile" width="800" />

Lets get the id in `FullPost`...
<img src="./assets/section-11/96.png" alt="smile" width="800" />

**Success**...We have loaded the relevant FullPost by passing the postID property using `this.props.match.params.id`
<img src="./assets/section-11/97.png" alt="smile" width="800" />

### Issue
1. If we click on `NewPost` we load the NewPost form but we also load the single post.
<img src="./assets/section-11/98.png" alt="smile" width="800" />

**Do you know why this happens ??**

# S11 | Parsing Query Parameters & the Fragment
---

<img src="./assets/section-11/99.png" alt="smile" width="800" />
<img src="./assets/section-11/100.png" alt="smile" width="800" />
<img src="./assets/section-11/101.png" alt="smile" width="800" />
<img src="./assets/section-11/102.png" alt="smile" width="800" />

# S11 | Using Switch to Load a Single Route
---
## Objective
1. Solve the issue below :

### Issue
1. If we click on `NewPost` we load the NewPost form but we also load the single post.
<img src="./assets/section-11/98.png" alt="smile" width="800" />

## Lecture Snapshots
All routes are rendered if they match the path
<img src="./assets/section-11/103.png" alt="smile" width="800" />

**One Solution** - could be ...
<img src="./assets/section-11/104.png" alt="smile" width="800" />
<img src="./assets/section-11/105.png" alt="smile" width="800" />

But you cannot change the urls like above ... ?
<img src="./assets/section-11/106.png" alt="smile" width="800" />

**Second Solution** - could be to load one Route at a time using `Switch` component. This will only load the first Route that matches the path.
<img src="./assets/section-11/107.png" alt="smile" width="800" />

The order is important when using `Switch`. Now `/new-post` should not come after `/:id`.

# S11 | Navigating Programmatically
---
## Objective
1. See an alternative to using `Link` component to load a single post - Navigate programatically

## Lecture Snapshots
<img src="./assets/section-11/108.png" alt="smile" width="800" />
<img src="./assets/section-11/109.png" alt="smile" width="800" />
<img src="./assets/section-11/110.png" alt="smile" width="800" />

Navigate programatically - suppose you want to navigate after some http request or any other operation. You can use the history object and navigate programatically after the operation ends.
<img src="./assets/section-11/111.png" alt="smile" width="800" />

`push` method allows you to push a page on the top of the stack of pages because navigation is basically just a stack of pages.
<img src="./assets/section-11/112.png" alt="smile" width="800" />
<img src="./assets/section-11/113.png" alt="smile" width="800" />

# S11 | Additional Information Regarding Active Links
---
## Objective
1. Concept - sometimes due to the way `to` property is defined will make it hard for the active link styling to occur as expected. 

## Lecture Snapshots
<img src="./assets/section-11/114.png" alt="smile" width="800" />
In this case the root page link "Posts" will be active at first. But after cliking a single post the **Posts** link wont be active.

Can you recall why? 

# S11 | Understanding Nested Routes
---
## Objective
1. So far we have loaded individual Routes in a Component that was not loaded via Routing.
2. No we want to load a Route with a component loaded via Routing i.e nested Routing.  

## Lecture Snapshots
Before the `FullPost` Route was in the `Blog` Component
<img src="./assets/section-11/115.png" alt="smile" width="800" />

But now we want to load a single `FullPost` component inside the `Posts` component which is itself loaded via Routing
<img src="./assets/section-11/116.png" alt="smile" width="800" />
<img src="./assets/section-11/117.png" alt="smile" width="800" />

Import Route and FullPost
<img src="./assets/section-11/118.png" alt="smile" width="800" />

Use nested Route. You can use the Route component wherever you want in your application as long as the Component inside which you are using it is wrapped by the `BrowserRouter` component.
<img src="./assets/section-11/120.png" alt="smile" width="800" />
<img src="./assets/section-11/121.png" alt="smile" width="800" />

Clicking on a single post, the url updates but the single post is not loaded.
<img src="./assets/section-11/122.png" alt="smile" width="800" />
<img src="./assets/section-11/123.png" alt="smile" width="800" />

The reason is that now we have created a nested Route.
Single post will get loaded when the path is like ` path="/:id" ` which does not match with the Route path for which its parent Component (`Post`) loads i.e. `path = "/" exact`
<img src="./assets/section-11/124.png" alt="smile" width="800" />
<img src="./assets/section-11/125.png" alt="smile" width="800" />

We can solve this by removing exact and changing the order in the Switch. 
Thus not both the nested Route and its parent Route will match.
<img src="./assets/section-11/126.png" alt="smile" width="800" />

Now it works !
<img src="./assets/section-11/127.png" alt="smile" width="800" />

### Issue 
Suppose we have as 
<img src="./assets/section-11/128.png" alt="smile" width="800" />

Thus we need to change the link from where we navigate.

Before
<img src="./assets/section-11/129.png" alt="smile" width="800" />
Now
<img src="./assets/section-11/130.png" alt="smile" width="800" />

Before 
<img src="./assets/section-11/131.png" alt="smile" width="800" />
Now
<img src="./assets/section-11/132.png" alt="smile" width="800" /> 

Before
<img src="./assets/section-11/133.png" alt="smile" width="800" />
Now
<img src="./assets/section-11/134.png" alt="smile" width="800" />

Before
<img src="./assets/section-11/135.png" alt="smile" width="800" />
Now - we have to update this Route path
<img src="./assets/section-11/136.png" alt="smile" width="800" />

**But this is cumbersome. Can we get the current path dynamically? Yes!**
<img src="./assets/section-11/137.png" alt="smile" width="800" />

Now we have same behaviour but nested routing where the path is changed dynamically.
<img src="./assets/section-11/137.png" alt="smile" width="800" />


# S11 | Creating Dynamic Nested Routes
---
## Issue
When we click on different posts it does not load the clicked post(a new component) on each click. Although the url changes to reflect that the click is working.
<img src="./assets/section-11/127.png" alt="smile" width="800" />

Whats the problem ? 

## Objective
1. Solve the Issue above.

## Lecture Snapshots
React Router behind the scenes does not replace the component all the time.
In case you are loading a component in whihc you are already on  like we are here. 
<img src="./assets/section-11/139.png" alt="smile" width="800" />

In such a case it wont execute the `componentDidMount` hook again because the component is not mounting, its just updating.
<img src="./assets/section-11/140.png" alt="smile" width="800" />

Solution is to implement `componentDidUpdate` and a utility method `loadData` which gets called in both hooks : `didMount` and `didUpdate`:
<img src="./assets/section-11/141.png" alt="smile" width="800" />
<img src="./assets/section-11/142.png" alt="smile" width="800" />

But now the request is sent infinite times. Why ? 
<img src="./assets/section-11/143.png" alt="smile" width="800" />

The condition inside `loadData()` is not correct.
We are checking if our id changed in the `props.id` which is never set.
We need to check the Router props forwarded.
<img src="./assets/section-11/144.png" alt="smile" width="800" />
<img src="./assets/section-11/145.png" alt="smile" width="800" />

We have to update this everywhere where we refer `props.id`
<img src="./assets/section-11/146.png" alt="smile" width="800" />
etc...

How to convert a string to a number ? (shortcut)
<img src="./assets/section-11/147.png" alt="smile" width="800" />
by adding a `+` sign in front.

**Now its fixed ! Great !!**
<img src="./assets/section-11/148.png" alt="smile" width="800" />


# S11 |  Redirecting Requests
---
## Objective
1. Redirect the user when they enter a url.

## Lecture Snapshots

**Solution-1** - render same Component for different paths
<img src="./assets/section-11/149.png" alt="smile" width="800" />

**Solution-2** - the `Redirect` component.
<img src="./assets/section-11/150.png" alt="smile" width="800" />
<img src="./assets/section-11/151.png" alt="smile" width="800" />

If you use outside the Switch statement `from` cannot be specified.

# S11 | Conditional Redirects
---
## Objective
Redirect conditionally after some http reques 

## Lecture Snapshots
Submitted state property
<img src="./assets/section-11/152.png" alt="smile" width="800" />

Set it to true once the http post request is made.
<img src="./assets/section-11/153.png" alt="smile" width="800" />

Conditionally redirect..
<img src="./assets/section-11/154.png" alt="smile" width="800" />

Result is we get redirected once we submit a new post...
<img src="./assets/section-11/155.png" alt="smile" width="390" /> **==>** <img src="./assets/section-11/156.png" alt="smile" width="390" />


# S11 | Using the History Prop to Redirect (Replace)
---
## Objective
Instead of the changing routes conditionally we can use the history props to push a new page after some operation finished.

## Lecture Snapshots
Using the history prop to push new page. So the back button takes us back to the last visted page.
<img src="./assets/section-11/157.png" alt="smile" width="800" />
<img src="./assets/section-11/158.png" alt="smile" width="800" /> 

Redirect replaces the current page and does as below...
<img src="./assets/section-11/159.png" alt="smile" width="800" />

# S11 |  Working with Guards
---
## Objective
We want to guard some of our Routes so that only authenticated user can access those.

## Lecture Snapshots
Suppose we want to make sure that `NewPost` cannot be reached...
<img src="./assets/section-11/160.png" alt="smile" width="800" />

We can simply render this conditionally...
<img src="./assets/section-11/161.png" alt="smile" width="800" />
<img src="./assets/section-11/162.png" alt="smile" width="800" />
<img src="./assets/section-11/163.png" alt="smile" width="800" />

The last case in the Switch kicks in and redirects when no matching Route is found.
<img src="./assets/section-11/164.png" alt="smile" width="800" />
This is a guard.

Another alternative is to give the logic inside the Component we want to guard.
<img src="./assets/section-11/165.png" alt="smile" width="800" />
<img src="./assets/section-11/166.png" alt="smile" width="800" />

# S11 |  Handling the 404 Case (Unknown Routes)
---
## Objective
Render some dummy content for unknown Routes.

## Lecture Snapshots
Use the Route without using the `path` property.
<img src="./assets/section-11/167.png" alt="smile" width="800" />
<img src="./assets/section-11/168.png" alt="smile" width="800" />

It wont work together with the root path
<img src="./assets/section-11/169.png" alt="smile" width="800" />

# S11 | Loading Routes Lazily (Optional)
---
## Objective
We want to load the code of a **Route** on demand when we really need it.
Advanced feature used in bigger apps.

## Lecture Snapshots
<img src="./assets/section-11/170.png" alt="smile" width="800" />

Loading NewPost upfront might not be required.
<img src="./assets/section-11/171.png" alt="smile" width="800" />

Code Splitting
<img src="./assets/section-11/172.png" alt="smile" width="800" />
<img src="./assets/section-11/173.png" alt="smile" width="800" />
<img src="./assets/section-11/174.png" alt="smile" width="800" />
<img src="./assets/section-11/175.png" alt="smile" width="800" />

We want to load the NewPost component dynamically 
<img src="./assets/section-11/176.png" alt="smile" width="800" />


Old way of importing
<img src="./assets/section-11/177.png" alt="smile" width="800" />
<img src="./assets/section-11/178.png" alt="smile" width="800" />

The Async function requirese an argument 
<img src="./assets/section-11/179.png" alt="smile" width="800" />

Dynamically import Newpost only when the `AsyncNewPost` gets rendered on the screen.
<img src="./assets/section-11/180.png" alt="smile" width="800" />

Using the hoc
<img src="./assets/section-11/181.png" alt="smile" width="800" />
<img src="./assets/section-11/182.png" alt="smile" width="800" />

See the 1 chunk bundle for NewPost loaded when NewPost was clicked.
<img src="./assets/section-11/183.png" alt="smile" width="800" />

# S11 | Lazy Loading with React Suspense (16.6)
---
## Objective
Using React.lazy and Suspense to do code splitting and lazy loading of Component code bundles on demand. 

## Lecture Snapshots
We want to load these paths only when we need them
<img src="./assets/section-11/185.png" alt="smile" width="800" />
<img src="./assets/section-11/184.png" alt="smile" width="800" />
<img src="./assets/section-11/186.png" alt="smile" width="800" />

Lets modify the render() method...
Using `Suspense` component.
<img src="./assets/section-11/187.png" alt="smile" width="800" />
<img src="./assets/section-11/188.png" alt="smile" width="800" />
<img src="./assets/section-11/189.png" alt="smile" width="800" />
<img src="./assets/section-11/190.png" alt="smile" width="800" />
<img src="./assets/section-11/191.png" alt="smile" width="800" />

We can also use the Suspense component in conditional rendering...
<img src="./assets/section-11/192.png" alt="smile" width="800" />
<img src="./assets/section-11/193.png" alt="smile" width="800" />
<img src="./assets/section-11/194.png" alt="smile" width="800" />

This only works for client side rendered application, not a server side rendered app.
Also use this technique for bigger chunks of code.

# S11 | Routing and Server Deployment
--- 
## Objective


## Lecture Snapshots
The server should always return the index.html page even for unknown requests. This then allows the React application to take over which knows the Routes. 
<img src="./assets/section-11/195.png" alt="smile" width="800" />

We need to set the base path for application root urls as below, which is a sub-directory.
<img src="./assets/section-11/196.png" alt="smile" width="800" />

**How?**
The default setting is as below: 
<img src="./assets/section-11/197.png" alt="smile" width="800" />
<img src="./assets/section-11/198.png" alt="smile" width="800" />

# S11 | Assignment 
---
## Question
<img src="./assets/section-11/199.png" alt="smile" width="800" />

## Answer
1. Add Routes
<img src="./assets/section-11/200.png" alt="smile" width="800" />
<img src="./assets/section-11/201.png" alt="smile" width="800" />
<img src="./assets/section-11/202.png" alt="smile" width="800" />
<img src="./assets/section-11/203.png" alt="smile" width="800" />
<img src="./assets/section-11/204.png" alt="smile" width="800" />
<img src="./assets/section-11/205.png" alt="smile" width="800" />

2. Add Navigation 
<img src="./assets/section-11/206.png" alt="smile" width="800" />
<img src="./assets/section-11/207.png" alt="smile" width="800" />

Style the link differently
<img src="./assets/section-11/208.png" alt="smile" width="800" />
<img src="./assets/section-11/209.png" alt="smile" width="800" />
<img src="./assets/section-11/210.png" alt="smile" width="800" />

3. Make the Courses clickable and load the Course component in the place of courses. 
- push page manually through code
- using the Link component

<img src="./assets/section-11/211.png" alt="smile" width="800" />
<img src="./assets/section-11/212.png" alt="smile" width="800" />
<img src="./assets/section-11/213.png" alt="smile" width="800" />
<img src="./assets/section-11/214.png" alt="smile" width="800" />
<img src="./assets/section-11/215.png" alt="smile" width="800" />
<img src="./assets/section-11/216.png" alt="smile" width="800" />
<img src="./assets/section-11/217.png" alt="smile" width="800" />

Load the Course `Component`
<img src="./assets/section-11/218.png" alt="smile" width="800" />
<img src="./assets/section-11/219.png" alt="smile" width="800" />
<img src="./assets/section-11/220.png" alt="smile" width="800" /> 

4. Pass the courseID to the Course page and outpuut it there.
<img src="./assets/section-11/221.png" alt="smile" width="800" />
<img src="./assets/section-11/222.png" alt="smile" width="800" />
<img src="./assets/section-11/223.png" alt="smile" width="800" />
<img src="./assets/section-11/224.png" alt="smile" width="800" />

Output CourseID
<img src="./assets/section-11/225.png" alt="smile" width="800" />s
<img src="./assets/section-11/226.png" alt="smile" width="800"/>
<img src="./assets/section-11/228.png" alt="smile" width="800" />
<img src="./assets/section-11/227.png" alt="smile" width="800" />
<img src="./assets/section-11/229.png" alt="smile" width="800" />

5. Pass the title 

Pass 2 params
<img src="./assets/section-11/230.png" alt="smile" width="800" />
<img src="./assets/section-11/232.png" alt="smile" width="800" />
<img src="./assets/section-11/233.png" alt="smile" width="800" />
<img src="./assets/section-11/234.png" alt="smile" width="800" />

Use query params
<img src="./assets/section-11/230.png" alt="smile" width="800" />
<img src="./assets/section-11/235.png" alt="smile" width="800" />
<img src="./assets/section-11/236.png" alt="smile" width="800" />
<img src="./assets/section-11/237.png" alt="smile" width="800" />
<img src="./assets/section-11/238.png" alt="smile" width="800" />
<img src="./assets/section-11/239.png" alt="smile" width="800" />

Parse the query param...
parsing has to be done in the Course.js file
<img src="./assets/section-11/240.png" alt="smile" width="800" />
<img src="./assets/section-11/241.png" alt="smile" width="800" />
<img src="./assets/section-11/242.png" alt="smile" width="800" />

<img src="./assets/section-11/243.png" alt="smile" width="800" />
<img src="./assets/section-11/244.png" alt="smile" width="800" />
<img src="./assets/section-11/245.png" alt="smile" width="800" />
<img src="./assets/section-11/246.png" alt="smile" width="800" />
<img src="./assets/section-11/247.png" alt="smile" width="800" />

6. Load the Course component as a nested component.
# 22 min 
<img src="./assets/section-11/248.png" alt="smile" width="800" />
<img src="./assets/section-11/249.png" alt="smile" width="800" />
<img src="./assets/section-11/250.png" alt="smile" width="800" />

Course loaded beneath our courses
<img src="./assets/section-11/251.png" alt="smile" width="800" />

But it does not really update the title even though the title updates in the url.
Reason is we parse the title in componentDidMount but the component is not unmounted and remounted 
<img src="./assets/section-11/252.png" alt="smile" width="800" />
<img src="./assets/section-11/253.png" alt="smile" width="800" />
<img src="./assets/section-11/254.png" alt="smile" width="800" />

Infinite loop world..
<img src="./assets/section-11/255.png" alt="smile" width="800" />
<img src="./assets/section-11/256.png" alt="smile" width="800" />
<img src="./assets/section-11/257.png" alt="smile" width="800" />

7. Add a 404 error page 
<img src="./assets/section-11/258.png" alt="smile" width="800" />
<img src="./assets/section-11/259.png" alt="smile" width="800" />

Catch All Route
<img src="./assets/section-11/260.png" alt="smile" width="800" />
<img src="./assets/section-11/261.png" alt="smile" width="800" />

8. Redirect
<img src="./assets/section-11/262.png" alt="smile" width="800" />