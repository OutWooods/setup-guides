### On Github

1. Go onto travis ci and then find the repo - activate it

2. Add a .travis.yml file to tell it what to do 
os:
  - linux

language: php

php:
  - '7.1'

before_script:
  - travis_retry composer self-update
  - travis_retry composer install --prefer-source --no-interaction --no-suggest
  - cp .env.travis .env
  - php artisan key:generate
  - yes | php artisan migrate
  - php artisan passport:keys
  - nvm install 11.15.0
  - npm install npm@latest -g
  - npm install

script:
  - vendor/bin/phpunit --coverage-text
  - npm run production

3. Add a .env.travis file 
APP_NAME=ExampleLaravelApplication
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_LOG_LEVEL=debug
APP_URL=http://localhost
DB_CONNECTION=sqlite
DB_DATABASE=:memory:
DB_USERNAME=homestead
DB_PASSWORD=secret
BROADCAST_DRIVER=log
CACHE_DRIVER=file
SESSION_DRIVER=file
SESSION_LIFETIME=120
QUEUE_DRIVER=sync
REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379
MAIL_DRIVER=log
MAIL_HOST=smtp.mailtrap.io
MAIL_PORT=2525
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null

4. And then push - hopefully it should all work!
