Friends List with Ruby in Rails

- Configuration:
    - instalation
    - creating project
    - rails new 'project_name'

- Creating the first webpage:
    - rails g controller home index
    - Creating about page -> manualy
    - Header -> manualy
    - 'Link to' in HTML using Rails -> '<% %>' -> Ruby code embebed into HTML

- Creating DB table with scaffold (CRUD):
    - rails g scaffold friends first_name:string last_name:string email:string phone:string twitter:string
    - rails db:migrate

- Styling app with bootstrap

- Devise User Managament
    - Add "gem 'devise', '~> 4.9', '>= 4.9.4'" on GemFile
    - bundle install
    - rails g devise:views
    - rails g devise user
    - rails db:migrate

- Style Devise Views

- Associations
    - user has_many friends
    - friend belongs_to user
    - rails g migration add_user_id_to_friends user_id:integer:index
        -> add user id to the friends table
    - rails db:migrate
    - Add in function 'friend_params' of 'friends_controller.rb' in 'permit': ':user_id'
    - Add 'before_actions' to verify only the correct user can do changes

- Showing only what belongs to current user:
    - <% if friend.user == current_user %>

- Style Modifications

- Fun With the Controller
    - Every page (view) has it respective controller, and you can acess its variables from the view
    - It allows you than separate the view from the hard code, front from back end

- Git, Github and Heroku
    - Heroku
        - Install
            - npm install -g heroku
            - heroku --version
            - heroku login
            - heroku create
            - heroku rename 'yourwebsitename'
            - heroku keys:add
        
        - Change the developement DB to a production DB
            - Add:
                'group :production do
                    gem 'pg', '~> 1.5', '>= 1.5.9'
                    #gem 'rails_12factor', '0.0.2'
                end'
                to 'Gemfile'
            - Move 'gem "sqlite3", ">= 1.4"' to development group

        -   Certifique-se de que as configurações no arquivo config/environments/production.rb estejam corretas. Por exemplo, verifique se o host está configurado corretamente:
            - config.action_mailer.default_url_options = { host: 'your-app-name.herokuapp.com' }

        - Push to Heroku
            - git push heroku main

        - Migrate DB to production
            - heroku run rails db:migrate

 
