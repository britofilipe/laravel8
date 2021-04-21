<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400"></a></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

# Aplicação Docker + Laravel 8

## Instalação

#### Step 1 - Change the ownership of the laravel-web directory to the non-root user.
```bash
$ sudo chown -R $USER:$USER ~/laravel-web
```

#### Step 2 - Run the Docker Containers
```bash
$ docker-compose up -d
$ docker-compose exec app bash
$ php artisan key:generate
$ php artisan config:cache
```

#### Step 3 - Configure a MySQL user
```bash
$ docker-compose exec db bash
# The password you set in the db service in the docker-compose file.
$ mysql -u root -p
# create a user and password for the laravel_web database. The password you set in .env file.
$ GRANT ALL ON laravel_web.* TO 'laraveldocker'@'%' IDENTIFIED BY 'your_strong_laravel_docker_password';
$ FLUSH PRIVILEGES;
```
#### Step 4 - Test the Communication between Laravel Application Code and the MySQL Database
```bash
$ docker-compose exec app bash
$ php artisan migrate
```
	