# Twig Plugin for Kirby CMS

<img src="doc/kirby-twig.png" width="200" alt="">

-   Adds support for [Twig templates](http://twig.sensiolabs.org/) to [Kirby CMS](https://getkirby.com/) (3.0+).
-   PHP templates still work, you don’t have to rewrite them if you don’t want to.


## What it looks like

Before:

```php
<?php /* site/templates/hello.php */ ?>
<h1><?= $page->title() ?></h1>
<ul>
<?php foreach ($page->children() as $child): ?>
  <li><a href="<?= $child->url() ?>"><?= $child->title() ?></li>
<?php endforeach; ?>
</ul>
```

After:

```twig
{# site/templates/hello.twig #}
<h1>{{ page.title }}</h1>
<ul>
{% for child in page.children %}
  <li><a href="{{ child.url }}">{{ child.title }}</li>
{% endfor %}
</ul>
```


## Installation

### Download

Download and copy this repository to `/site/plugins/kirby-twig`.

### Git submodule

```
git submodule add https://github.com/mgfagency/kirby-twig.git site/plugins/kirby-twig
```

### Composer

```
composer require mgfagency/kirby-twig
```

****

## Usage

### Page templates

Now that the plugin is installed and active, you can write Twig templates in the `site/templates` directory. For example, if the text file for your articles is named `post.txt`, you could have a `post.twig` template like this:

```twig
{% extends 'layout.twig' %}
{% block content %}
  <article>
    <h1>{{ page.title }}</h1>
    {{ page.text.kirbytext | raw }}
  </article>
{% endblock %}
```

See the `{% extends '@templates/layout.twig' %}` and `{% block content %}` parts? They’re a powerful way to manage having a common page layout for many templates, and only changing the core content (and/or other specific parts). Read [our Twig templating guide](doc/guide.md) for more information.

## Options

You can find a full list of options in the [options documentation](doc/options.md).

****

## More documentation

- [Twig templating guide for Kirby](doc/guide.md)
- [Available options](doc/options.md)
- [Using your own functions in templates](doc/functions.md)
- [Using Kirby Twig with other plugins](doc/plugins.md)
- [Rendering a template in PHP: the `twig` helper](doc/twighelper.md)
- [Displaying Twig errors](doc/errors.md)

## License

[MIT](LICENSE.md)

## Credits

- Twig library: Fabien Potencier and contributors / [License](https://github.com/twigphp/Twig/blob/2.x/LICENSE)
- Twig plugin for Kirby 2: Florens Verschelde
