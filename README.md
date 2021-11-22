<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400"></a></p>


## Schedule daily backups

Add to your Kernel.php

// app/Console/Kernel.php
$schedule->command('backup:clean')
  ->dailyAt('03:00')
  ->runInBackground();

$schedule->command('backup:run', ['--only-db'])
  ->dailyAt('04:00')
  ->runInBackground();

## Run backup manualy

You can backup your app by running:

php artisan backup:run
If you want to backup to a specific disk instead of all disks, run:

php artisan backup:run --only-to-disk=name-of-your-disk
If you only need to backup the db, run:

php artisan backup:run --only-db
If you only need to backup the files, and want to skip dumping the databases, run:

php artisan backup:run --only-files

Enjoy!
