# Currency Crafter

Console application that parses a file containing transaction data and calculates commissions applying various rules,
such as customer type, transaction currency, and so on.

## Requirements:
- [Docker](https://docs.docker.com/engine/install/ubuntu/)
- [Docker-compose](https://docs.docker.com/compose/install/)

## Installation:
 - Open your console and run `cp -u .env.example .env` 
 - Run `docker-compose up` to build a container
 - Run `docker-compose exec php-fpm /bin/bash` to pass into container
 - Inside container run `composer install` to install dependencies

## Xdebug

To enable xdebug on local machine (PHPStorm):
* Go to Settings -> PHP -> Servers and set up new server with name "php-fpm" and host "172.22.0.1".<br>
Also set up path mappings: /application to main folder

## Run command:
 - Inside container run `php bin/console app:calculate-fees test.csv`

## Run test:
 - Inside container run `php vendor/bin/phpunit`
 
## Env variables:
 - `CURRENCY_EXCHANGE_API_URL` - Api url of currency rates
 - `DEFAULT_CURRENCY` - Default currency
 - `DEFAULT_RATES_MODE` - Determines whether it is necessary to make requests to the currency rate server. Enum (`1`, `0`). Default `1`
 - `DEFAULT_RATES_FILE_PATH` - Default currency rates file path
 - `DEPOSIT_PERCENT_FEE` - Percent of deposit amount to charge
 - `PRIVATE_CLIENT_FREE_AMOUNT` - Weekly free withdrawals
 - `PRIVATE_CLIENT_FREE_WITHDRAWS` - Weekly withdrawal limit
 - `FEE_PRECISION` - Number of decimal places when rounding
 - `WITHDRAW_FEE_FOR_PRIVATE_CLIENT` - Commission fee for private clients
 - `WITHDRAW_FEE_FOR_BUSINESS_CLIENT` - Commission fee for business clients 
