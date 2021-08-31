# Putting it All Together: Client-Server Communication

## Learning Goals

- Understand how to communicate between client and server using fetch, and how
  the server will process the request based on the URL, HTTP verb, and request
  body
- Debug common problems that occur as part of the request-response cycle

## Introduction

Just like the last lesson, we've got code for a React frontend and Rails API
backend set up. This time though, it's up to you to use your debugging skills to
find and fix the errors!

To get the backend set up, run:

```console
$ bundle install
$ rails db:migrate db:seed
$ rails s
```

Then, in a new terminal, run the frontend:

```console
$ npm install --prefix client
$ npm start --prefix client
```

Confirm both applications are up and running by visiting
[`localhost:4000`](http://localhost:4000) and viewing the list of toys in your
React application.

## Deliverables

In this application, we have the following features:

- Display a list of all the toys
- Add a new toy when the toy form is submitted
- Update the number of likes for a toy
- Donate a toy to Goodwill (and delete it from our database)

The code is in place for all these features on our frontend, but there are some
problems with our API! We're able to display all the toys, but the other three
features are broken.

Use your debugging tools to find and fix these issues.

There are no tests for this lesson, so you'll need to do your debugging in the
browser and using the Rails server logs and `byebug`.

**Note**: You shouldn't need to modify any of the React code to get the
application working. You should only need to change the code for the Rails API.

As you work on debugging these issues, use the space in this README file to take
notes about your debugging process. Being a strong debugger is all about
developing a process, and it's helpful to document your steps as part of
developing your own process.

## Your Notes Here

- Add a new toy when the toy form is submitted

  - How I debugged: First I tried to add a new toy and found a 500 server error. Then I checked the routes.rb to makes sure the create route existed. Then I checked the create method in the ToysController. There, I found that Toy was pluralized on accident. So, I changed it. I tested again, and it worked this time. 

- Update the number of likes for a toy

  - How I debugged: I clicked the like button to see what error I would get. I wasn't sure what this error meant exactly so I added a byebug. I checked to see what the toy was in the update function and when I clicked the button it was correct. So, I knew that wasn't the problem. Therefore, the problem must be the json this is trying to read from, which made me realize that no json is being returned, which makes sense as to why the error was with the json. After adding the return, it worked.

- Donate a toy to Goodwill (and delete it from our database)

  - How I debugged: I checked to see what error it was and saw it was a 404, which means that it was not found. I saw that the destroy function existed and looked right, so I checked the routes.rb to make sure there was a route for it. I found that there wasn't, so I added the route. I added it to the routes, and it worked. 
