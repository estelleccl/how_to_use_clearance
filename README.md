#Clearance
Clearance is a simple Ruby on Rails authentication with email & password.

To setup Clearance, visit this page: https://github.com/thoughtbot/clearance or follow the following steps below:

1. add ``` gem ‘clearance’ ``` into Gemfile

2. run ``` bundle ``` in the terminal

3. run ``` rails generate clearance:install ``` in the terminal 

4. add ``` config.action_mailer.default_url_options = { host: 'localhost:3000' } ``` into ```config/environments/development.rb ``` and also ``` config/environments/test.rb ```

5. add the following code into ```views/home/index.html.erb ``` or your navigation bar or your root page
  ```   
    <% if signed_in? %>
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

6. run ``` bundle exec rake db:migrate ``` in the terminal

7. make sure the following code ``` root 'home#index' ``` is in config/routes.rb (*optional if you have root page)

8. run ``` rails g migration add_three_columns_to_users_for_clearance``` in the terminal
    
9. go to ``` db/migrate``` and find ```<timestamps>_add_three_columns_to_users_for_clearance.rb ```add the following code into the file:
  ``` 
    add_column :users, :encrypted_password, :string
    add_column :users, :remember_token, :string
    add_column :users, :confirmation_token, :string 
```

10. run ``` bundle exec rake db:migrate  ``` in the terminal

11. make sure users table has encrypted_password, confirmation_token, remember_token columns


#References
1. https://github.com/thoughtbot/clearance


