# Northflank Ruby on Rails migration example

<a target="_blank" rel="noopener noreferrer" href="https://www.northflank.com">
    <img alt="Northflank" align="right" src="/media/logo.svg" width="35%" />
</a>

Deploy this Rails with migrations example easily on Northflank with this [one-click template](). This will create a new project in your account with the required services and database Addon.

Alternatively you can clone this repository and follow along with [this guide]().

This repository consists of a Ruby on Rails application configured to use a [Northflank Postgres Addon](https://northflank.com/dbaas/managed-postgresql).

#### Authorizing hosts

This application has been configured to [authorize hosts](https://guides.rubyonrails.org/configuring.html#actiondispatch-hostauthorization) passed via the environment variable `NF_HOSTS`. You can change this, if necessary, by manually setting the environment variable or changing `config.hosts` in the Ruby environments in `config/environments`.

#### External database

This application has been [configured to use an external database](https://guides.rubyonrails.org/configuring.html#configuring-a-database) in `config/database.yml` using the secrets from a Northflank Postgres Addon, as shown in `.env.example`. On the Northflank platform these secrets can be added to a service as environment variables, or by [using a secret group linked to the Addon](https://northflank.com/docs/v1/application/databases-and-persistence/connect-database-secrets-to-workloads).

It is recommended that you deploy separate Addons for development and production, and should therefore supply different connection details in the secrets depending on the environment. You are advised to use the Northflank-created database (exported in the secret `NF_POSTGRES_DATABASE`), as this is what will be backed up and restored if using [the native backup method](https://northflank.com/docs/v1/application/databases-and-persistence/backup-restore-and-import-data).

You will only need to run `rails db:create` or `rake db:create` to create the `test` database, or if you are not using the default Northflank-created database.

See the quick start below for instructions on deploying and using the Northflank Postgres Addon.

## About Rails

[Ruby on Rails](https://rubyonrails.org/), or Rails, is a server-side web application framework written in Ruby under the MIT License. Rails is a model–view–controller framework, providing default structures for a database, a web service, and web pages.

This example project uses Rails version 7.0.4 running on Ruby version 3.1.2.

## Quick start 🚀

To follow this quick start, clone this repository to your local machine and install [Ruby version 3.1.2](https://www.ruby-lang.org/en/documentation/installation/). You can also use [rbenv](https://github.com/rbenv/rbenv) or [rvm](https://rvm.io/) to manage your Ruby installations (recommended). 


1. **Install Rails version 7.0.4.**

    ```shell
    gem install rails --version 7.0.4
    ```

2. **Install PostgreSQL.**

   [Download and install PostgreSQL](https://www.postgresql.org/download/) on your machine for development. You may also need to [install libpq](https://www.postgresql.org/docs/14/libpq.html) separately.


3. **Install packages.**

   Navigate into the project directory and install gems with:

    ```shell
    # Install using bundle:
    bundle install
    ```


4. **Initialise the database**

   [Deploy a PostgreSQL Addon](https://northflank.com/docs/v1/application/databases-and-persistence/deploy-postgresql-on-northflank) on Northflank, and copy the required connection details to a `.env` file in your project (see `.env.example`) for the required secrets. [Forward](https://northflank.com/docs/v1/api/forwarding) the database Addon to your local machine for development (you can copy the command from the Addon's overview).

   Run `rails db:create` and `rails db:migrate` to create the `test` database and run the initial migration.


6. **Start developing.**
   
   Run the development server:
    
    ```shell
    rails server
    ```
   
    The live development website should now be available at [http://localhost:3000](http://localhost:3000), connected to your development database Addon.


7. **Deploy to Northflank.**

   Push your repository to a git service and build it on Northflank. You can either use [a combined service](https://northflank.com/docs/v1/application/getting-started/build-and-deploy-your-code) if you just want to build and deploy one branch, or use [a build service](https://northflank.com/docs/v1/application/build/build-code-from-a-git-repository) with a separate [deployment service](https://northflank.com/docs/v1/application/run/run-an-image-continuously) if you want to build multiple branches and pull requests.
   Using a build service also allows you to run [migrations as jobs](https://docs.build.run/docs/v1/application/release/handle-runtime-migrations#migrate-using-a-job-triggered-by-ci), or deploy multiple microservices from a monorepo. 


8. **Run migrations.**

   See [the guide]() on running migrations for Rails applications.