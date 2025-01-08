Friends List with Ruby in Rails

- Configuration:
    - instalation
    - creating project

- Creating the first webpage:
    - rails g controller home index
    - Creating about page
    - Header
    - Link to in HTML using Rails

- Creating DB table with scaffold:
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
