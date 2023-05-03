# PHP Codesniffer Base Config

## Usage:

1. Make the following additions to the composer.json file
   1. Add repository
        ```json
        "repositories": [
           {
              "type": "vcs",
              "url": "https://github.com/singularit-de/php-codesniffer-base-config.git"
           }
       ]
      ```
   2. Add necessary packages 
      ```json
      "require": {
         ...
         "singular-it/php-codesniffer-base-config": "dev-master"
         "squizlabs/php_codesniffer": "^3.7"
         ...
      },
      ```
2. Run ``composer update``
3. Create a file in your projects root directory called ``phpcs.xml`` with the following content:
    ```xml
   <?xml version="1.0"?>
    <ruleset>
        <description>Project-specific ruleset</description>
        <rule ref="vendor/singular-it/php-codesniffer-base-config/src/phpcs.xml"/>
    
        <!-- Add project-specific rules below -->
    </ruleset>
   ```
   Alternatively, for php versions smaller than 8, include ``vendor/singular-it/php-codesniffer-base-config/src/phpcs-before-php8.xml`` instead

=> You can now run phpcs via ``vendor/bin/phpcs path/to/check`` and are able to extend the phpcs.xml file to add project-specific rules.