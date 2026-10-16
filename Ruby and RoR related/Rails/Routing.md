# Routing
We define all the endpoints and their corresponding controller actions in `configroutes.rb`.

hashrocket style is less used and JSON style is mostly used. However we decided to include hashrocket style also since it's still very widely used.

The above code could be written like this also.

`get "/articles", to: "articles#list"`

Coming back to routing, here is how it will work:

1. When a user visits http://localhost:3000/articles Rails looks at the config/routes.rb file and tries to find first pattern matching with /articles.
2. In this case, we have only one entry and its value corresponds to articles#list.
Rails will split that string into two parts: articles and list.
3. The first part, articles, will be used to search for a controller with a matching name. In this case, Rails will be searching for the class ArticlesController.
The second part, list, will be considered as the name of the method to be called.
4. Now, Rails will run the method list defined inside ArticlesController class and the result will be returned to the client.

## Dynamic segments in routes
Let's say that we want to see the details of the book **The Fountainhead**.

The URL could look like http://localhost:3000/books/the-fountainhead. What should the route configuration be for this?

We can have something like this:

`get "/books/the-fountainhead" => "books#the_fountainhead"`
If we have thousands of books, or if the books are dynamically added, this strategy will not scale. We can't manually keep making an entry in the routes file for each book.

**Dynamic Segments** are there to rescue us in such situations. This is how we define routes using Dynamic segment approach.

`get "/books/:id" => "books#show"`\
In the above case when user visits /books/the-fountainhead, Rails will send the request to show action inside BooksController class.

Also, Rails will make the request path segment corresponding to :id available in params method. The value of params behaves like a hash. We will learn more about the usage of params in the next chapter.

We can access the value of :id from show action like this:
`
class BooksController < ApplicationController
  def show
    book_name = params[:id]
    # get the book details from the database
  end
end
`
## Root URL
Root URL determines what to respond when a user tries to load the home page of our application. In our case, it will be http://localhost:3000.

We will define route to the root URL like this:

`root to: "home#welcome"`\
In the above case when a user visits the homepage, the welcome action in the HomeController will be triggered.
