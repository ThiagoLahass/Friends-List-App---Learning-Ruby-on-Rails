
# Friends List with Ruby on Rails

## Overview
This project is a **Friends List Application** built with **Ruby on Rails**. It allows users to manage their friends' information (first name, last name, email, phone, twitter handle) and includes user authentication and CRUD (Create, Read, Update, Delete) functionality.

---

## Table of Contents
- [Configuration](#configuration)
- [Creating the First Webpage](#creating-the-first-webpage)
- [Database Setup](#database-setup)
- [Styling](#styling)
- [User Authentication](#user-authentication)
- [Associations](#associations)
- [Showing User-Specific Data](#showing-user-specific-data)
- [Git, GitHub, and Heroku Setup](#git-github-and-heroku-setup)

---

## Configuration

### Installation
To set up the project locally, follow these steps:

1. **Install Ruby on Rails**:
    ```bash
    gem install rails
    ```

2. **Create a new Rails project**:
    ```bash
    rails new 'project_name'
    ```

---

## Creating the First Webpage

1. **Generate the controller**:
    ```bash
    rails g controller home index
    ```

2. **Creating an About Page**:  
    Create an "about" page manually.

3. **Adding Header**:  
    Add a custom header to your homepage manually.

4. **Linking to Pages in HTML**:  
    Use embedded Ruby (`<% %>`) to add dynamic content in your HTML files.

---

## Database Setup

### Creating DB Table with Scaffold (CRUD)

1. **Generate the scaffold for friends**:
    ```bash
    rails g scaffold friends first_name:string last_name:string email:string phone:string twitter:string
    ```

2. **Migrate the database**:
    ```bash
    rails db:migrate
    ```

---

## Styling

### Add Bootstrap to Style the Application

1. **Install Bootstrap**:  
    Follow the [Bootstrap installation guide for Rails](https://getbootstrap.com/docs/4.5/getting-started/introduction/).

---

## User Authentication

### Install Devise for User Management

1. **Add Devise gem** to `Gemfile`:
    ```ruby
    gem 'devise', '~> 4.9', '>= 4.9.4'
    ```

2. **Install the gem**:
    ```bash
    bundle install
    ```

3. **Generate Devise views**:
    ```bash
    rails g devise:views
    ```

4. **Generate the User model**:
    ```bash
    rails g devise user
    ```

5. **Migrate the database**:
    ```bash
    rails db:migrate
    ```

---

## Associations

### Setting up Associations Between User and Friend

1. **Define associations** in models:
    - `User` model:  
      ```ruby
      has_many :friends
      ```

    - `Friend` model:  
      ```ruby
      belongs_to :user
      ```

2. **Add user_id to friends table**:
    ```bash
    rails g migration add_user_id_to_friends user_id:integer:index
    ```

3. **Migrate the database**:
    ```bash
    rails db:migrate
    ```

4. **Modify `friend_params` method** to permit `user_id`:
    ```ruby
    params.require(:friend).permit(:first_name, :last_name, :email, :phone, :twitter, :user_id)
    ```

5. **Add `before_action` in the `friends_controller.rb`** to ensure only the correct user can make changes.

---

## Showing User-Specific Data

To show only friends that belong to the current user, use the following conditional in your views:

```erb
<% if friend.user == current_user %>
```

This ensures that each user only sees their own friends.

---

## Git, GitHub, and Heroku Setup

### Heroku Setup

1. **Install Heroku CLI**:
    ```bash
    npm install -g heroku
    ```

2. **Login to Heroku**:
    ```bash
    heroku login
    ```

3. **Create a new Heroku app**:
    ```bash
    heroku create
    ```

4. **Rename your Heroku app (optional)**:
    ```bash
    heroku rename 'yourwebsitename'
    ```

5. **Add your Heroku SSH key**:
    ```bash
    heroku keys:add
    ```

---

### Configuring the Production Database

1. **Edit the `Gemfile`** to use PostgreSQL for production:
    ```ruby
    group :production do
        gem 'pg', '~> 1.5', '>= 1.5.9'
    end
    ```

2. **Move `sqlite3` gem to the development group**:
    ```ruby
    gem 'sqlite3', '>= 1.4'
    ```

3. **Ensure correct host configuration in `config/environments/production.rb`**:
    ```ruby
    config.action_mailer.default_url_options = { host: 'your-app-name.herokuapp.com' }
    ```

---

### Deploying to Heroku

1. **Push the code to Heroku**:
    ```bash
    git push heroku main
    ```

2. **Migrate the production database**:
    ```bash
    heroku run rails db:migrate
    ```

---


## Acknowledgements

- [Ruby on Rails](https://rubyonrails.org/)
- [Heroku](https://www.heroku.com/)
- [Bootstrap](https://getbootstrap.com/)