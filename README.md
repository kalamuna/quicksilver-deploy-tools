# Quicksilver Deployment Tools

This Quicksilver project is used for automation of post-deployment tasks on Pantheon platform.

### Installation

This project is designed to be included from a site's `composer.json` file, and placed in its appropriate installation directory by [Composer Installers](https://github.com/composer/installers). 

It has to also include custom quick-silver installer as composer installer doesn't support the quicksilver-script type.

In order for this to work, you should have the following in your composer.json file:

```json
{
  "require": {
    "composer/installers": "^1.0.20",
    "rvtraveller/qs-composer-installer": "1.0"
  },
  "extra": {
    "installer-paths": {
      "web/private/scripts/quicksilver/{$name}/": ["type:quicksilver-script"]
    }
  }
}
```

The project can be included by using the command:

`composer require kalamuna/quicksilver-deploy-tools`

Don't forget to update the `pantheon.yml` file for your Drupal 8/9 installation.

### Example `pantheon.yml`

Here's an example of what your `pantheon.yml` would look like if this were the only Quicksilver operation you wanted to use.

```yaml
api_version: 1

workflows:
  sync_code:
    after:
      - type: webphp
        description: Import configuration from .yml files
        script: private/scripts/quicksilver-deploy-tools/postdeploy.php
```
