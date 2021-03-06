# OPENFAAS PHP8 Template

This is a PHP 8.0 template for [OpenFaaS, the serverless functions project.](https://github.com/openfaas/faas)

Comes with PHP 8.0.5 and Composer 2. Templates are built using the latest minor version of the major release.

| Modules (by default) |
| ------------- |
| Core, date, libxml, openssl, pcre, sqlite3, zlib, ctype, curl, dom, fileinfo, filter, ftp, hash, iconv, json, mbstring, SPL, PDO, pdo_sqlite, session, posix, readline, Reflection, standard, SimpleXML, Phar, tokenizer, xml, xmlreader, xmlwriter, mysqlnd, sodium |

## Install:


```shell
cd <project-dir>
faas-cli template pull https://github.com/mattwithoos/openfaas-php8
faas-cli new <function-name> --lang php8
```

Note that faas-cli doesn't appear to keep a registry or cache of third-party templates, so running `template pull` will store the template in the immediate `./template` dir. Move it, or, update your .yml if this doesn't suit.

In the near future I'll submit the template to the official repo, making the process easier.

## Usage

You will find in the newly created directory `my-function`:

- `src/Handler.php` : entrypoint
- `php-extension.sh` : is for installing PHP extensions if needed
- `composer.json` : is for dependency management

## Extra Extensions

If you need to install an extension, check out the `src/php-extension.sh` file;

You can also refer to the PHP Docker image [documentation](https://github.com/docker-library/docs/blob/master/php/README.md#how-to-install-more-php-extensions) for additional instructions on the installation and configuration of extensions

## Private Composer Auth

In some cases, you may need to use private composer repositories - using the `faas-cli` you can pass in
a build argument during build, for example;

```
faas-cli build -f ./functions.yml \
  --build-arg COMPOSER_AUTH='{"bitbucket-oauth": {"bitbucket.org": {"consumer-key": "xxxxxxxx","consumer-secret": "xxxxxxx"}}}'
```
See more information [here](https://getcomposer.org/doc/05-repositories.md#git-alternatives).

That way you can pass in tokens for Composer, if necessary, GitHub tokens to get around rate-limit issues.
