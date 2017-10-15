---
layout: post
title:      "Knock! Knock! Who's there? Authenticate!"
date:       2017-10-15 23:34:02 +0000
permalink:  knock_knock_whos_there_authenticate
---


In this day and age everybody is concerned with security. With Ruby on Rails, authentication is handled on the server side using gems like BCrypt. In other words, if signin isn't correct, Rails will never serve the appropriate page. The user signs in, gets authenticated, and presto they're on their way. But React on the other hand is a little bit of a different beast. 

Since React is on the front side, how does it go about authenticating the user? Enter JWT(JSON Web Token). This article is about [JWT itself](https://jwt.io/). Ok now that you read all about JWT, how do you use it with a React/Rails app? We could use the ruby jwt gem by adding `gem 'jwt'` to our gemfile. But then we would have to write encode and decode methods in our session model, plus some other details. What about on user creation? What then? Implementation isn't impossible, but it is on the difficult side. 

As a relatively new developer, I wanted to find something a little more simple to implement JWT. We've come to what this article is about ... the Knock gem. [Here's](https://github.com/nsarno/knock/tree/v2) an explanation of Knock in detail. Without further adieu, let's get to it. 

First things first let add the `gem 'knock'` and `gem 'bcrypt'` to our gemfile and `bundle install`. In our User model now make sure you have 

```ruby
class User < ActiveRecord::Base
 has_secure_password
end
```

Knock uses `has_secure_password` to authenticate User. Then run the install generator.
```ruby
rails generate knock:install
```

This will create the following initializer `config/initializers/knock.rb`. This file contains all the information about the existing configuration options. If you don't use an external authentication solution like Auth0, you also need to provide a way for users to authenticate so now run 

```ruby
rails generate knock:token_controller user
```

This will generate the controller `user_token_controller.rb` and add the required route to your config/routes.rb file. But I'll come back to this controller.

Include the `Knock::Authenticatable` module in your `ApplicationController`
```ruby
class ApplicationController < ActionController::API
 include Knock::Authenticatable
end
```

You can now restrict access to your controllers like this
```ruby
class SecuredController < ApplicationController
 before_action :authenticate_user

 def index
  # etc...
 end
 
   # etc...

end
```

Let's take a step back and go back to the `user_token_controller.rb`. What does this file include when created? 
```ruby
class UserTokenController < Knock::AuthTokenController
end
```
That's it. Whaaaaaaatttttt! It doesn't get much simpler then that. If you look at the documentation on github you can see all the methods that `user_token_controller` inherits by looking at the `auth_token_controller.rb` file. The generated knock initializer file contains things like the given token lifetime, the signature algorithm and a few more to help curate the gem the way you like. 

Let's test this out and see if we can return a JWT token. Create new user in rails console. From terminal in rails directory run command `rails s -p 3001` to run a rails server on port 3001. Once created from your terminal run this curl command with your provided email and password values. 
```
curl -X POST -H 'Content-type: application/json' -d '{"auth":{"email":"testing@gmail.com", "password":"3115"}}' http://localhost:3001/user_token
```
Which should return a json object similar to this
```
{"jwt":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE1MDgxOTM2MDQsInN1YiI6M30.5couZ7EIXNklaqN_SrA0g1crJukpk8R_k98ESf7bsbM"}
```

This works great for signing in a user and returning a token. But this example is for a `User` that's already created. What about returning a token when initially creating a `User`? There's a simple solution for this. In your `UserController` under your `create` action include this code
```ruby
def create
 user = User.new(user_params)
 if user.valid? && user.save
  token = Knock::AuthToken.new(payload: { sub: user.id })
	render json: token, status: 200
 end
end
```
What you've done here is created a new JWT token to return to your React app. So now what? Where do you store this returned token, since you need to include it with subsequent requests? LocalStorage maybe? Ah that's for a post on another day. 
