#Errors and Solution for Clearance gem

1. can only see <b><i>`You're in the users#new. This file is located in app/views/users/new.html.erb`</i></b>. 
   When click on SignUp buttom 
   
   	Solution: 
		```delete views/users folder ```

2. <b><i>NoMethodError in Clearance::UsersController#create undefined method `encrypted_password=' for #<User:0x007f9631da31c0> </i></b>

  	Solution:
		``` add encrypted_password column to users table ```
	
3. <b><i>NoMethodError in Clearance::UsersController#create undefined method `remember_token=' for #<User:></i></b>

	Solution:
		``` add remember_token column to users table```
4. <b><i>NoMethodError in Clearance::PasswordsController#create
undefined method `confirmation_token=' for #<User:0x007fc961cb6998> </i></b>
	
	Solution:
		```add confirmation_token column to users table```

5. <b><i>Forget Password Feature unable to send email </i></b>
	
	Solution:
```
		a. please setup your smtp to send email
			i. gmail
				1. add the following code into config/development.rb

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
 
 				2. add ``` gem ‘figaro’ into Gemfile```
				3. bundle
 				4. add the following code into config/application.yml

					email_address: "<your email address>"
					email_password: "<password>"
				5. try your forget password feature again
				6. login your gmail
				7. go to https://www.google.com/settings/security/lesssecureapps
				8. Turn on Access for less secure apps
```

6. <b><i>ActiveRecord::StatementInvalid in SessionsController#create_from_omniauth Could not find table 'authentications' authentication = Authentication.find_by_provider_and_uid(auth_hash["provider"], auth_hash["uid"]) || Authentication.create_with_omniauth(auth_hash) </i></b>


	Solution:
		```create authentication table with uid,token and provider column```

7. <b><i>NoMethodError in SessionsController#create_from_omniauth
undefined method `friendly_name=' for #<User:></i></b>
	Solution:
		``` add ``` friendly_name ``` column to users table ```

8. <b><i>NoMethodError in SessionsController#create_from_omniauth
undefined method `picture =' for #<User:></i></b>

	Solution:
		``` add ``` picture ``` column to users table ```

9. <b><i>NoMethodError in SessionsController#create_from_omniauth
undefined method `friendly_name =' for #<User:></i></b>

	Solution:
		``` add ``` friendly_name ``` column to users table ```
10. <b><i>NoMethodError in SessionsController#create_from_omniauth
undefined method `last_name =' for #<User:></i></b>

	Solution:
		``` add ``` last_name ``` column to users table ```
11. <b><i>ActiveModel::MissingAttributeError in SessionsController#create_from_omniauth
    can't write unknown attribute `user_id</i></b>

	Solution:
		``` add ``` user_id ``` column to authentications table ```
