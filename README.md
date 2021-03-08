
# Desarrollo de una API con Ruby on rails


## Inicio Desarrollo de API 
```
rails new blogapi --api -T

cd blogapi

code .

rails s
```

## Configuraciones Gemas


* RSpec
* SHOULDA MATCHERS
* FACTORY BOT
* DATABASE CLEANER


### Configuración Gemfile

```
group :development, :test do
# Call 'byebug' anywhere in the code to stop execution and get a debugger console
  gem 'byebug', platforms: [:mri, :mingw, :x64_mingw]
  gem 'rspec-rails', '~> 3.5'
end

group :test do
  gem 'factory_bot_rails', '~> 4.0'
  gem 'shoulda-matchers', '~> 3.1'
  gem 'faker', '~> 1.9'
  gem 'database_cleaner', '~> 1.7'
end

$ bundle install

$ rails generate rspec:install
```


```
$ bundle exec rspec
```


```
shoulda-matchers

$ rails_helper.rb
# Line 8 Add additional requies below ...

Shoulda::Matchers.configure do |config|
  config.integrate do |with|
    with.test_framework :rspec

    # Keep as many of these lines as are necessary:
    with.library :active_record
    with.library :active_model
    with.library :action_controller
    with.library :rails
  end
end

$ bundle exec rspec

Dentro de RSpec.configure do |config|, agregar

  config.include FactoryBot::Syntax::Methods

  config.before(:suite) do
      DatabaseCleaner.strategy = :transaction
      DatabaseCleaner.clean_with(:truncation)
  end

  config.around(:each) do |example|
    DatabaseCleaner.cleaning do
      example.run
    end
  end


$ bundle exec rspec
```

### Crear carpetas para desarrollo TDD

```
mkdir spec/requests
touch spec/requests/healt_spec.rb
$ rails db:migrate
```



# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
