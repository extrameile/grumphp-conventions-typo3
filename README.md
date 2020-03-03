# What does it do

Provides a preconfigured grumphp setup for TYPO3 extensions that i write.   

# Usage

## Setup composer configuration

The configuration currently expects the package in some specific directories. Run these lines to setup composer accordingly. This will only take effect, if you run composer from the extension, not from your project and should thus be safe to use. Hint: the `git ignore` command is available after installing the git-extras (https://github.com/tj/git-extras/blob/master/Installation.md) package. Check your favourite package manager for it!

~~~shell
git ignore .Build composer.lock
composer config vendor-dir .Build/vendor
composer config bin-dir .Build/bin
composer config extra.typo3/cms.cms-package-dir "{\$vendor-dir}/typo3/cms"
composer config extra.typo3/cms.web-dir .Build/Web
~~~

## Install

~~~shell
composer config repositories.grumphp-conventions-typo3 vcs https://github.com/extrameile/grumphp-conventions-typo3.git
composer require --dev extrameile/grumphp-conventions-typo3 dev-master
~~~

## Configure grumphp

Create a grumphp.yml in your extension directory and insert this content:
~~~yaml
imports:
  - { resource: .Build/vendor/extrameile/grumphp-conventions-typo3/grumphp.yml }
~~~
or symlink it from this package
~~~bash
ln -s .Build/vendor/extrameile/grumphp-conventions-typo3/grumphp.yml .
~~~

## Running it

~~~shell
.Build/bin/grumphp run
~~~
