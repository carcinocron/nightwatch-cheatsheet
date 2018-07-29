# Checkboxes

## Assert Checked
```js
browser.expect.element('input[type=checkbox]').to.have.attribute('checked')
```
or
```js
  browser.getAttribute('input[type=checkbox]', 'checked', function (result) {
    this.assert.equal(typeof result, "object");
    this.assert.equal(result.status, 0, result.value&&result.value.message || 'Expected status 0 for success');
    this.assert.equal(result.value, true);
  });
```

## Assert Unchecked
```js
browser.expect.element('input[type=checkbox]').to.not.have.attribute('checked')
```
or
```js
  browser.getAttribute('input[type=checkbox]', 'checked', function (result) {
    this.assert.equal(typeof result, "object");
    this.assert.equal(result.status, 0, result.value&&result.value.message || 'Expected status 0 for success');
    this.assert.equal(result.value, null);
  });
```

## Notes

- `result.value` will be `true` for checked and `null` for unchecked (actual values, not strings).
- You can't add `.equal(true)` to `.to.have.attribute('checked')` because `equal` only accepts strings.
