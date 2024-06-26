# Quicksilver Deployment Tools

This Quicksilver project is used for automation of post-deployment tasks on Pantheon platform.

### Installation

This project is designed to be included from a site's `composer.json` file, and placed in its appropriate installation directory by [Composer Installers](https://github.com/composer/installers). 

The project can be included by using the command:

`composer require kalamuna/quicksilver-deploy-tools`

Don't forget to update the `pantheon.yml` file for your Drupal 8/9 installation.

### Example `pantheon.yml`

Here's an example of what your `pantheon.yml` would look like if this were the only Quicksilver operation you wanted to use.

```yaml
api_version: 1

workflows:
  deploy:
    after:
      - type: webphp
        description: Import configuration from .yml files
        script: private/scripts/quicksilver/quicksilver-deploy-tools/postdeploy.php
  sync_code:
    after:
      - type: webphp
        description: Import configuration from .yml files
        script: private/scripts/quicksilver-deploy-tools/postdeploy.php
```
