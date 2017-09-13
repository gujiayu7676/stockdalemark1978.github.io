---
layout: post
title:  "Bootcamp Complete - I Graduated!"
date:   2017-08-12 10:16:12 -0400
categories: 		
---
## I Graduated! Plus: Using OAuth2 With Laravel

I can hardly believe it, but bootcamp has come to an end. Not only has it come to an end, but I made it through!!

It has been a long, challenging, and very rewarding journey. There were days where I felt like Superman and days where I felt it would take me weeks to learn a couple simple lines of code.

# Using OAuth With Laravel

I haven't posted in a while as I've been swamped trying to make sure I was learning and keeping up with everything, but I wanted to take a second to go over something I learned while working with Laravel during our final group project.

If you are not familiar with Laravel, it is a PHP framework that does a TON of stuff to structure your project and help make things easier.

One particular aspect in which it helps is using OAuth2 in a project.

Laravel can setup authentication easily for traditional login forms for a site, but it can also help when using APIs.

The first thing that has to be done is to use something called "Passport" which is a part of the framework. In order to do this, you have to install Passport using Composer via the terminal:

    compser require laravel/passport

After that, you have to add Passport as a service provider in the providers array contained in the app.php file. You just need to type/paste this line in the providers array:

    Laravel\Passport\PassportServiceProvider::class,

After that, you want to be sure you run the migration feature of Laravel to migrate your database after you've registered the provider. Passport automatically makes its own database which will allow it to store clients and access tokens. In the terminal, type:

    php artisan migrate

Note that this will run your other migrations as well.

After migration, you need to use passports install command as this will generate secure access tokens. To do this, type the following:

    php artisan passport: install

Next, you have to the trait Laravel\Passport\HasApiTokens to your App\User model. This provides helper methods to allow inspection of the user's token and scopes. Find this portion in the User model and make it match:

    <?php

    namespace App;

    use Laravel\Passport\HasApiTokens;
    use Illuminate\Notifications\Notifiable;
    use Illuminate\Foundation\Auth\User as Authenticatable;

    class User extends Authenticatable
    {
        use HasApiTokens, Notifiable;
    }

Now you have to call the Passport::routes method contained in the boot method of yoru AuthServiceProvider. This method registers all necessary routes for issuing and revoking tokens, clients, and personal access tokens. Make sure your file matches this:

    <?php

    namespace App\Providers;

    use Laravel\Passport\Passport;
    use Illuminate\Support\Facades\Gate;
    use Illuminate\Foundation\Support\Providers\AuthServiceProvider as ServiceProvider;

    class AuthServiceProvider extends ServiceProvider
    {
        /**
        * The policy mappings for the application.
        *
        * @var array
        */
        protected $policies = [
            'App\Model' => 'App\Policies\ModelPolicy',
        ];

        /**
        * Register any authentication / authorization services.
        *
        * @return void
        */
        public function boot()
        {
            $this->registerPolicies();

            Passport::routes();
        }
    }


Lastly, you have to set the driver option of the api authentication guard to passport. This is located in the config/auth.php file. This tells your app to use Passport to authenticate API requests. This section you need to change should look like this:

        'guards' => [
        'web' => [
            'driver' => 'session',
            'provider' => 'users',
        ],

        'api' => [
            'driver' => 'passport',
            'provider' => 'users',
        ],
    ],

At this stage, there are different ways to go about issuing tokens. The simplest way that I'm currently aware of is creating a simple Vue backend area which allows you to easily create keys, which can then be used to get a token.

In order to get started with the Passport Vue components, you have to use this Artisan command:

    php artisan vendor:publish --tag=passport-components

This will create Vue components in your resources/assets/js/components directory. You also will need to register the components in your resources/assets/js/app.js file by adding the following:

    Vue.component(
        'passport-clients',
        require('./components/passport/Clients.vue')
    );

    Vue.component(
        'passport-authorized-clients',
        require('./components/passport/AuthorizedClients.vue')
    );

    Vue.component(
        'passport-personal-access-tokens',
        require('./components/passport/PersonalAccessTokens.vue')
    );

At this stage you have to run:

    npm run dev

That will recompile your assets. You can then place the components into any of your app's templates and create clients and tokens from that page.
