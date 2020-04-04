# Restful Blog 

Simple dynamic web app which uses RESTful routing to satisfy all CRUD funcitionalities.


## Technology Stack:
MongoDB, Express, Node, Semantic UI

## Workflow:

1. SETUP

    * create package.json containing  metadata (especially dependencies)using npm init command
    * install necessary node packages using npm (node package manager)
        - express - node framework
        - mongoose - js interface for interacting with mongodb
        - ejs - embedded js - dynamic templates
        - body-parser - to get our data from a form
        - method-override - to override post request to put in the edit form
    * create app.js (the main file) 
    * include packgaes using require
    * configure app
    * configure mongo database using mongoose
    * setup server
    * create partial templates (header, footer) and link with styles

2. MONGOOSE SCHEMA + MODEL CONFIG

3. RESTful ROUTES

    * index ("/blogs", GET)
        - redirect get "/" (home) to index
        - retrieve blogs from db
        - render index passing blogs
        - create inex template

    * new - form ("/blog/new", GET)
        - create render new template which displays a **form**
        - form will not create anything until the update route is done

    * create - action of the form ("/blog", POST)
        - get the data from the form (body-parser)
        - create blog (also includes into db)
        - callback function redirects to show

    * show ("/blogs/:id", GET)
        - find the blog with the id from the request
        - render the show template in the callback, passing found blog
        - create show template

    * edit ("/blogs/:id/edit", GET)
        - find the blog with the id from the request
        - render the edit template in the callback, passing found blog
        - create edit template (copy the form from new)
        - form will not create anything until the update route is done

    * update ("/blogs/:id", PUT)
        - create the route in app.js
        - set edit form action to redirect here
        - html forms only support get and post request 
        => we use method-override package to override post to put
        (we could just do post with different url, but we want to follow the useful RESTful routes pattern)
        - find the blog with the id from the request and update db
        (findByIdAndUpdate(id, new_date, callback))
        - callback function redirects to show

    * destroy ("/blogs/:id", DELTE)