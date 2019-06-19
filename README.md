# PHP git pre-commit hook

## About

This package allows the installation of a git hook pre-commit.
This hook will :

- Run [PHP Code Sniffer](https://github.com/squizlabs/PHP_CodeSniffer)
- Check for var_dump, die, etc left in the code
- Run prettier on js files @TODO

It checks only staged files.

Inspired by [Enforce code standards with composer, git hooks, and phpcs](http://tech.zumba.com/2014/04/14/control-code-quality/)

## Installation

Install `bpagoaga/precommit-symfony-1.4` with composer require command:

    composer require "bpagoaga/precommit-symfony-1.4"

Or alternatively, include a dependency for `bpagoaga/precommit-symfony-1.4` in your composer.json file manually:

```
{
    "require-dev": {
        "bpagoaga/precommit-symfony-1.4": "dev-master"
    }
}
```

To enable code sniff, аdd to `post-install-cmd` and `post-update-cmd` in `composer.json` installation script:

```
"scripts": {
    "post-install-cmd": [
        "sh ./lib/vendor/bpagoaga/precommit-symfony-1.4/src/setup.sh"
    ],
    "post-update-cmd": [
        "sh ./lib/vendor/bpagoaga/precommit-symfony-1.4/src/setup.sh"
    ]
}
```

Then run `composer install` or `composer update`. `pre-commit` hook will be installed or updated if it already exists.

## Usage

Run `git commit -m "..."` and pre-commit hook will check your committed files.

If needed, you can bypass the hook with the --no-verify option:

`git commit -m "..." --no-verify`
