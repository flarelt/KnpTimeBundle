# Friendly ago dates ("5 minutes ago")!

This bundle does one simple job: takes dates and gives you friendly "2 hours ago"-type messages. Woh!

```html+jinja
    Last edited {{ post.updatedAt|ago }}
    <-- Last edited 1 week ago -->
```

The date formatted can be translated into any language, and may are supported out of the box.

## INSTALLATION via Composer

    composer require knplabs/knp-time-bundle

## CONFIGURATION
Register the bundle:

```php
<?php
// app/AppKernel.php
public function registerBundles()
{
    $bundles = array(
        // ...
        new Knp\Bundle\TimeBundle\KnpTimeBundle(),
    );
    // ...
}
```

Enable the translation component if you haven't already done it:

```yaml
# app/config/config.yml
framework:
    # ...
    translator:      { fallback: %locale% } # uncomment this line if you see this line commented
```


## USAGE

In PHP!

```php
<?php
// Use the helper with Php
echo $view['time']->diff($dateTime); // returns something like "3 minutes ago"
```

In Twig!

```html+jinja
{{ someDateTimeVariable|ago }}
... or use the equivalent function
{{ time_diff(someDateTimeVariable) }}
```

### Note:

If you are using a different language code than two letters (en_US for example) then
should copy the TimeBundle's language files and rename the middle part according to your language:

    from:
    MyProject/vendor/bundles/Knp/Bundle/TimeBundle/Resources/translations/time.en.xliff
    MyProject/vendor/bundles/Knp/Bundle/TimeBundle/Resources/translations/time.fr.xliff

    to:
    MyProject/app/Resources/translations/time.en_US.xliff
    MyProject/app/Resources/translations/time.fr_FR.xliff

Don't forget to clear your cache afterwards.

