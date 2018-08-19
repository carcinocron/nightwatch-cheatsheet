# Laravel Dusk API translated to nightwatch

All examples assume css selectors and working knowledge of Laravel Dusk. 

Examples based on https://laravel.com/docs/5.6/dusk

## Dusk Selectors

As far as I know, there is not a dusk selector shorthand for nightwatch. Nightwatch will also not look for `[name="login-button"]` if you type in `login-button`.

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

## `waitForLocation ( $path /* not full URL, no query string */ )`

```php
$browser->waitForLocation('/dashboard');
```

```js
// I could not find a known equivalent,
// best to waitForElementVisible on the next page's dusk identifier
browser.waitForElementPresent('[dusk="dashboard"]', 5)
browser.assert.urlContains('/dashboard')
```

## `waitForText` 

```php
$browser->waitForText('Hello World');
```

```js
// also note that "contains" means "exact match",
// where the laravel example is a "contains" match.
// a more precise example needs to be found.
// Also, one that does not require specifying a parent element
// but thats not a big deal ATM
browser
    .expect.element('p')
    .text.to.contain('Hello World').before(5)
