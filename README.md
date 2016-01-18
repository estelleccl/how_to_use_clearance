#Clearance
Clearance is a simple Ruby on Rails authentication with email & password.

To setup Clearance, visit this page: https://github.com/thoughtbot/clearance or follow the following steps below:

1. add ``` gem ‘clearance’ ``` into Gemfile

2. run ``` bundle ``` in the terminal

3. run ``` rails generate clearance:install ``` in the terminal 

4. add ``` config.action_mailer.default_url_options = { host: 'localhost:3000' } ``` into ```config/environments/development.rb ``` and also ``` config/environments/test.rb ```

5. add the following code to ```views/home/index.html.erb ```

``` if signed_in? %>
      Signed in as: <%= current_user.email %>
      <%= button_to 'Sign out', sign_out_path, method: :delete %>
    <% else %>
      <%= link_to 'Sign in', sign_in_path %>
      <%= link_to 'Sign Up', sign_up_path %>
    <% end %>

    <div id="flash">
      <% flash.each do |key, value| %>
        <div class="flash <%= key %>"><%= value %></div>
      <% end %>
    </div>
```

#References
1. https://github.com/thoughtbot/clearance


