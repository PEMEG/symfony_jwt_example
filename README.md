# Symfony 6 JWT example
> Simple example of symfony 6 JWT authentication that can be used as the basis of a project.

## Table of contents
* [Technologies](#technologies)
* [Setup](#setup)
* [Usage](#usage)

## Technologies
- Symfony (6.1.3)
- Symfony CLI (5.4.13)
- PHP (8.1.6)
- MariaDB (10.4.24)
- Composer (2.3.10)
- LexikJWTAuthenticationBundle (2.16.0)

## Setup
### 1. Edit .env file
Phrases that need to be changed in .env:
```bash
# .env
APP_SECRET=CHANGE_ME
DATABASE_URL="mysql://USERNAME:PASSWORD@127.0.0.1:3306/DATABASE?serverVersion=mariadb-10.4.24"
JWT_PASSPHRASE=CHANGE_ME
```
### 2. Install packages
```bash
composer install
```
### 3. Generate keypair
> **⚠️ OpenSSL needed**
```bash
php bin/console lexik:jwt:generate-keypair
```
### 4. Init doctrine
```bash
php bin/console doctrine:migrations:migrate
```
### 5. Run symfony
```bash
symfony serve
```

## Usage
> Protip:  use Postman

To get the jwt token, you have to send credentials in json format to _/api/login_check_ by POST.
```yaml
{
    "email": "your_email",
    "password": "your_password"
}
```
If you want to validate token, send him inside "Bearer Token" to _/home_. It should returns information about token.
```yaml
{
    "iat": 1661017461,
    "exp": 1661021061,
    "roles": [
        "ROLE_USER"
    ],
    "email": "email@email.com"
}
```