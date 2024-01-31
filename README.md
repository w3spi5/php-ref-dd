Fork
--------------
This is a fork of digitalnature/php-ref with updates from [Juan Manuel Cabello](https://github.com/fellowgeek/php-ref) to include PHP8 adaptations, modified to use `dd()` like in Laravel Framework.

> REF, or `dd()` is a nicer alternative to PHP's [`print_r`](http://php.net/manual/en/function.print-r.php) / [`var_dump`](http://php.net/manual/en/function.var-dump.php) / or `r()` itself functions

Demo
-------

[DEMO from `digitalnature/php-ref`](http://dev.digitalnature.eu/php-ref/)

Installation
------------

Start by [installing composer](https://getcomposer.org/doc/01-basic-usage.md#installation).
Next do:

    $ composer require w3spi5/php-ref-dd

Requirements
------------

PHP 8.x+

Now tell composer to download the bundle by running:

Composer will install the bundle to the directory `vendor/w3spi5`.

Usage
-------

Basic example:

    // include the class (not needed if project runs with Composer because it's auto-loaded)
    require '/full/path/to/ref.php';

    // display info about defined classes
    dd(get_declared_classes());

    // display info about global variables
    dd($GLOBALS);

To print in text mode you can use the `ddt()` function instead:

    ddt($var);

To terminate the script after the info is dumped, prepend the bitwise NOT operator:

    ~dd($var);   // html
    ~ddt($var);  // text

Prepending the error control operator (@) will return the information:

    $output = @dd($var);   // html
    $output = @ddt($var);  // text

Keyboard shortcuts (javascript must be enabled):

- `X` - collapses / expands all levels

To modify the global configuration call `ref::config()`:

    // example: initially expand first 3 levels
    ref::config('expLvl', 3);

Currently available options and their default values:

| Option                    | Default             | Description
|:------------------------- |:------------------- |:-----------------------------------------------
| `'expLvl'`                | `1`                 | Initially expanded levels (for HTML mode only). A negative value will expand all levels
| `'maxDepth'`              | `6`                 | Maximum depth (`0` to disable); note that disabling it or setting a high value can produce a 100+ MB page when input involves large data
| `'showIteratorContents'`  | `FALSE`             | Display iterator data (keys and values)
| `'showResourceInfo'`      | `TRUE`              | Display additional information about resources
| `'showMethods'`           | `TRUE`              | Display methods and parameter information on objects
| `'showPrivateMembers'`    | `FALSE`             | Include private properties and methods
| `'showStringMatches'`     | `TRUE`              | Perform and display string matches for dates, files, json strings, serialized data, regex patterns etc. (SLOW)
| `'formatters'`            | `array()`           | Custom/external formatters (as associative array: format => className)
| `'shortcutFunc'`          | `array('r', 'rt')`  | Shortcut functions used to detect the input expression. If they are namespaced, the namespace must be present as well (methods are not  supported)
| `'stylePath'`             | `'{:dir}/ref.css'`  | Local path to a custom stylesheet (HTML only); `FALSE` means that no CSS is included.
| `'scriptPath'`            | `'{:dir}/ref.js'`   | Local path to a custom javascript (HTML only); `FALSE` means no javascript (tooltips / toggle / kbd shortcuts require JS)
| `'showUrls'`              | `TRUE`              | Gets information about URLs. Setting to false can improve performance (requires showStringMatches to be TRUE)

License
-------

This library is released under the MIT license. See the complete license in the LICENSE file.
