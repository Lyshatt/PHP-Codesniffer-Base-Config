# PHP Codesniffer Base Config

## Basic Information:
### About the PHP Codesniffer Package:
PHP_CodeSniffer is a set of two PHP scripts; the main phpcs script that tokenizes PHP, JavaScript and CSS files to detect violations of a defined coding standard, and a second phpcbf script to automatically correct coding standard violations. PHP_CodeSniffer is an essential development tool that ensures your code remains clean and consistent.

=> Documentation: https://github.com/squizlabs/PHP_CodeSniffer/wiki

### About this Project:
This Project basically provides a set of predefined php coding standard rules that can be used and extended as described below.

## Installation:

1. Make the following additions to the composer.json file
   1. Add repository:
        ```json
        "repositories": [
           {
              "type": "vcs",
              "url": "https://github.com/singularit-de/php-codesniffer-base-config.git"
           }
       ]
      ```
   2. Add the package:
      ```json
      "require": {
         ...
         "singular-it/php-codesniffer-base-config": "dev-master"
         ...
      },
      ```
2. Run ``composer install`` or ``composer update`` to install the new dependency.
3. Create a file in your projects root directory called ``phpcs.xml`` with the following content:
    ```xml
   <?xml version="1.0"?>
    <ruleset>
        <description>Project-specific ruleset</description>
        <rule ref="./vendor/singular-it/php-codesniffer-base-config/src/phpcs.xml"/>
    
        <!-- Add project-specific rules below -->
    </ruleset>
   ```
   Alternatively, for php versions smaller than 8, the  rule should look like this: ``<rule ref="./vendor/singular-it/php-codesniffer-base-config/src/phpcs-before-php8.xml"/>``

## CLI Usage:

- You can now run phpcs via ``vendor/bin/phpcs path/to/check`` and are able to extend the phpcs.xml file to add project-specific rules.
- As PHP Codesniffer also includes the "PHP Code Beautifier and Fixer", you can use ``vendor/bin/phpcbf path/to/fix`` to automatically fix some smells.

## PhpStorm Setup:
Find the official description here: https://www.jetbrains.com/help/phpstorm/using-php-code-sniffer.html . Basically:
- In the Settings under PHP > Quality Tools > PHP_Codesniffer click on the three dots after the "Configuration"-field, which opens a separate view. Here you will find the "PHP_CodeSniffer path" field and the "Path to phpcbf" field. The path to phpcs should be set to something like this `C:\...\vendor\bin\phpcs.bat` and the path to phpcbf to something like this `C:\...\vendor\bin\phpcbf.bat`.
- Go back to PHP > Quality Tools > PHP_Codesniffer and choose "custom" as coding standard, which causes an input field to appear. If the option "custom" is not available, try closing and re-opening the settings. In this input field enter the path to your own phpcs.xml file in your project's root directory.
- Go to PHP > Quality Tools > External Formatters and code PHP Code Beautifier and Fixer.

=> You should now be able to see IDE highlighting for code smells and hovering should give you the option to fix them, if they are automatically fixable.
