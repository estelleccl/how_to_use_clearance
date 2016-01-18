#Errors and Solution for Clearance gem

1. ``` can only see ``` You're in the users#new. This file is located in `app/views/users/new.html.erb` ```
   when click on SignUp buttom ```
Solution: 
```delete views/users folder ```

2. ``` NoMethodError in Clearance::UsersController#create undefined method `encrypted_password=' for #<User:0x007f9631da31c0> ```
Solution:
			add encrypted_password column to users table
Problem:
NoMethodError in Clearance::UsersController#create
undefined method `remember_token=' for #<User:0x007f9636b5c420>
Solution:
		add remember_token column to users table
Problem:
NoMethodError in Clearance::PasswordsController#create
undefined method `confirmation_token=' for #<User:0x007fc961cb6998>
Solution:
		add confirmation_token column to users table

Problem:
Forget Password Feature unable to send email
please setup your smtp to send email
gmail
add the following code into config/development.rb

ActionMailer::Base.delivery_method = :smtp

  ActionMailer::Base.smtp_settings = {
   :address => "smtp.gmail.com",
   :port => 587,
   :domain => "gmail.com",
   :user_name => ENV["email_address"],
   :password => ENV["email_password"],
   :authentication => :plain,
   :enable_starttls_auto => true
}
 add ``` gem ‘figaro’ into Gemfile```
 bundle
 add the following code into config/application.yml

email_address: "<your email address>"
email_password: "<password>"
try your forget password feature again
login your gmail
go to https://www.google.com/settings/security/lesssecureapps
Turn on Access for less secure apps
Problem:
ActiveRecord::StatementInvalid in SessionsController#create_from_omniauth Could not find table 'authentications'
authentication = Authentication.find_by_provider_and_uid(auth_hash["provider"], auth_hash["uid"]) || Authentication.create_with_omniauth(auth_hash)




Solution:
create authentication table with uid,token and provider column
Problem:
NoMethodError in SessionsController#create_from_omniauth
undefined method `friendly_name=' for #<User:0x007f9162b346b0>




Solution:
add ``` friendly_name ``` column to users table
Problem:
NoMethodError in SessionsController#create_from_omniauth
undefined method `picture =' for #<User:0x007f9162b346b0>




Solution:
add ``` picture ``` column to users table


