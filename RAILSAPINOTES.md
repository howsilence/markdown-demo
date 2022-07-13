# Creating a Rails API from Scratch
#### [Back to Demo Page](/README.md)

Throughout this section we'll be focusing on how the client-server communication process works, as well as some challenges involved in communicating between two separate applications.

In this lesson, we'll start by building the Rails backend from scratch and talk through some of the typical configuration when creating a new **Rails API.**

We can use `rails new` to generate a new Rails application. We'll run that same command with some added options to optimize our Rails app: `--api --minimal`

```
=> rails new dvd-shop --api --minimal
```

- `--api` flag creates the new application with some additional API-specific configurations and will skip the code for generating `.erb` files with `ActionView`
- `--minimal` flag skips many of the additional Rails features that won't be needed in an API such as code for sending emails and processing images.

One of the main features of the frontend application will be to display a list of movies. For that feature we'll want our API to handle a *GET* request to */movies*. To get that request working we'll also need a *model* to interact with the database and a *migration* the generate the corresponding database for this table.

For the `Movie`*model* we'll want the following attributes:

- title: string
- year: integer
- length: integer
- director: string
- description: string
- poster_url: string
- category: string
- discont: boolean
- female_director: boolean

We could create the route, model, controller and migration individually, but since this kind of operation is extremely common for a Rails dev we can simply use the build in:

### Rails G Resource

```rb
$ rails g resource Movie title year:integer length: integer director description poster_url category title discount: boolean female_director:boolean
```

This command will:

- Generate a migration for creating a movies table with specified attributes
- Generate a Movie model.rb file
- Generate a MoviesController controler.rb file
- Add resources :movies to the routes.rb file

### Remember Models are Singular, Controllers are Plural!

This is a powerful command so make sure you measure twice before you code once and make sure you only use `rails g resource` if you really NEED all the code it generates.

### [Back to Demo Page](/home.md)