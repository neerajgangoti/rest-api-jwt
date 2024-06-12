# Rest-api-jwt

# Step 1
composer create-project laravel/laravel rest-api

# Step 2: Set Database Details

Open the .env file and set the

DB_CONNECTION=mysql

DB_HOST=127.0.0.1

DB_PORT=3306

DB_DATABASE=rest_apis
DB_USERNAME=root
DB_PASSWORD=

# Step 3: Install api.php

php artisan install:api

# Step 4. Install JWT Package

	
composer require php-open-source-saver/jwt-auth

php artisan vendor:publish --provider="PHPOpenSourceSaver\JWTAuth\Providers\LaravelServiceProvider"

php artisan jwt:secret

config/auth.php

'defaults' => [
        'guard' => 'api',
        'passwords' => 'users',
    ],
 
'guards' => [
        'web' => [
            'driver' => 'session',
            'provider' => 'users',
        ],
 
        'api' => [
            'driver' => 'jwt',
            'provider' => 'users',
        ],
    ],


# Step 5: Create the AuthController

php artisan make:controller AuthController
