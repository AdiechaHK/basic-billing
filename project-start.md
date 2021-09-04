# Get starter kit
```
curl -s https://laravel.build/example-app | bash
mv example-app gaurang-billing
cd gaurang-billing
```
[Referance](https://laravel.com/docs/8.x/starter-kits#laravel-breeze-installation)




# Set env for database

- make sure your database is running correctly
- and created database with name `gaurang_billing`

Then you need to set database name, username, passwrod in `.env` file.

```
DB_CONNECTION=mysql
DB_HOST=localhost
DB_PORT=3306
DB_DATABASE=gaurang_billing
DB_USERNAME=root
DB_PASSWORD=root
```

# Database migration

```
php artisan migrate
```

# Setup breeze (for frontend) 

*Make sure you are using current/stable version of node, here I used node v12*

```
composer require laravel/breeze --dev
php artisan breeze:install vue
npm install
npm run dev
php artisan migrate

```