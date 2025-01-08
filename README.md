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

- Exibindo apenas o que pertence ao usuário atual:
    - <% if friend.user == current_user %>

- Style Modifications