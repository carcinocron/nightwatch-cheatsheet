# Laravel Dusk API translated to nightwatch

All examples assume css selectors and working knowledge of Laravel Dusk. 

Examples based on https://laravel.com/docs/5.6/dusk

## Dusk Selectors

As far as I know, there is not a dusk selector shorthand for nightwatch.

```html
<button dusk="login-button">Login</button>
```

```php
$browser->click('@login-button');
```

```js
browser.click('[dusk="login-button"]');
```

## click

```php
$browser->click('.login-page .container div > button');
```

```js
browser.click('.login-page .container div > button');
```
