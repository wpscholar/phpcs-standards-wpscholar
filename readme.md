# PHP Code Sniffer Standards for WordPress Development

An advanced configuration of the WordPress coding standards for plugin and theme development.

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
    "vendor/bin/phpcbf . --standard=WPScholar"
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
  <config name="testVersion" value="8.0-"/>
  <config name="minimum_supported_wp_version" value="6.0"/>
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


### PHPStorm Setup

1. Open up the preferences panel.
2. Go to "Languages & Frameworks" > "PHP" > "Code Sniffer".
3. Ensure the "Configuration" section has "Local" set in the dropdown. Click the "..." button.
4. Set the "PHP Code Sniffer path" to be "{projectRoot}/vendor/bin/phpcs" where "{projectRoot}" is the actual path of
   your project root.
5. Hit "OK".
6. Go to "Editor" > "Inspections" in the preference panel.
7. Click on "PHP Code Sniffer validation" under the "PHP" > "Quality tools" section.
8. Hit the refresh button next to the "Coding Standard" field on the right.
9. Select "Newfold" from the dropdown.
10. Hit "OK" to exit the preferences panel.