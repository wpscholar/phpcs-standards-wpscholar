# PHP Code Sniffer Standards for WordPress Development

An advanced configuration of the WordPress coding standards for plugin and theme development.

This ruleset is configured to support WordPress version 5.8+ and PHP version 7.0+.

## Usage

- Install [Composer](https://getcomposer.org/)
- Run `composer init` to set up Composer for your project.
- Run `composer require wpscholar/phpcs-standards-wpscholar` to install the coding standards.
- Run `vendor/bin/phpcs . --standard=WPScholar` from your project root to check your code.
- Optionally, add a script to your `composer.json` file so you can just run `composer run lint` to check your code.

```json
"scripts": {
  "lint": [
    "vendor/bin/phpcs . --standard=WPScholar"
  ],
  "clean": [
    "vendor/bin/phpcbf . --standard=Newfold"
  ]
}
```

## Additional Notes
- Append the `-s` flag to see the internal names of the rules.
- Add `--runtime-set testVersion 8.0-` to check PHP version 8.0 or greater.
- Add a custom `phpcs.xml` file to your project to customize the ruleset or your desired configuration.

```xml
<?xml version="1.0"?>
<ruleset name="Project Rules">
  <rule ref="WPScholar" />
  <config name="testVersion" value="7.0-"/>
  <config name="minimum_supported_wp_version" value="5.8"/>
</ruleset>
```

### Additional Documentation
- https://github.com/squizlabs/PHP_CodeSniffer
- https://github.com/PHPCompatibility/PHPCompatibilityWP
- https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards

## IDE Integration

Some IDE integrations of PHPCS will fail to register your ruleset since it doesn't live in your project root. In order
to rectify this, place phpcs.xml at your project root:

```xml
<?xml version="1.0"?>
<ruleset name="Project Rules">
    <rule ref="WPScholar"/>
</ruleset>
```
