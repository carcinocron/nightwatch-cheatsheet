# nightwatch-cheatsheet

## Laravel Dusk

If you need the laravel dusk API translated to nightwatch: [Laravel Dusk](dusk.md)

## General

```
this.nightwatchTest = function (browser) {
  //Expect
  browser.expect.element('#main').to.be.present;
  browser.expect.element('#main').to.be.visible;
  browser.expect.element('#main').text.to.equal('The Night Watch');
  browser.expect.element('#main').text.to.contain('The Night Watch');
  browser.expect.element('#main').to.have.css('display').which.equals('block');
  browser.expect.element('#main').text.to.not.equal('The Night Watch');
  browser.expect.element('#main').text.to.not.contain('The Night Watch');
  browser.expect.element('#main').to.have.css('display').which.does.not.equal('block');
  browser.expect.element('#main').text.to.contain('The Night Watch').before(1000);
  browser.expect.element('#main').text.to.not.contain('The Night Watch').after(500);
  browser.expect.element('#q').to.be.an('input');
  browser.expect.element('#q').to.be.an('input', 'Testing if #q is an input');
  browser.expect.element('#w').to.be.a('span');
  browser.expect.element('body').to.have.attribute('data-attr');
  browser.expect.element('body').to.not.have.attribute('data-attr');
  browser.expect.element('body').to.not.have.attribute('data-attr', 'Testing if body does not have data-attr');
  browser.expect.element('body').to.have.attribute('data-attr').before(100);
  browser.expect.element('body').to.have.attribute('data-attr').equals('some attribute');
  browser.expect.element('body').to.have.attribute('data-attr').not.equals('other attribute');
  browser.expect.element('body').to.have.attribute('data-attr').which.contains('something');
  browser.expect.element('body').to.have.attribute('data-attr').which.matches(/^something\ else/);
  browser.expect.element('#main').to.have.css('display');
  browser.expect.element('#main').to.have.css('display', 'Testing for display');
  browser.expect.element('#main').to.not.have.css('display');
  browser.expect.element('#main').to.have.css('display').before(100);
  browser.expect.element('#main').to.have.css('display').which.equals('block');
  browser.expect.element('#main').to.have.css('display').which.contains('some value');
  browser.expect.element('#main').to.have.css('display').which.matches(/some\ value/);
  browser.expect.element('#weblogin').to.be.enabled;
  browser.expect.element('#main').to.not.be.enabled;
  browser.expect.element('#main').to.be.enabled.before(100);
  browser.expect.element('#main').to.be.present;
  browser.expect.element('#main').to.not.be.present;
  browser.expect.element('#main').to.be.present.before(100);
  browser.expect.element('#main').to.be.selected;
  browser.expect.element('#main').to.not.be.selected;
  browser.expect.element('#main').to.be.selected.before(100);
  browser.expect.element('#main').text.to.equal('The Night Watch');
  browser.expect.element('#main').text.to.not.equal('The Night Watch');
  browser.expect.element('#main').text.to.equal('The Night Watch').before(100);
  browser.expect.element('#main').text.to.contain('The Night Watch');
  browser.expect.element('#main').text.to.match(/The\ Night\ Watch/);
  browser.expect.element('#q').to.have.value.that.equals('search');
  browser.expect.element('#q').to.have.value.not.equals('search');
  browser.expect.element('#q').to.have.value.which.contains('search');
  browser.expect.element('#q').to.have.value.which.matches(/search/);
  browser.expect.element('#main').to.be.visible;
  browser.expect.element('#main').to.not.be.visible;
  browser.expect.element('#main').to.be.visible.before(100);
 
  //Assert
  browser.assert.attributeContains('#someElement', 'href', 'google.com');
  browser.assert.attributeEquals("body", "data-attr", "some value");
  browser.assert.containsText("#main", "The Night Watch");
  browser.assert.cssClassPresent("#main", "container");
  browser.assert.cssClassNotPresent("#main", "container");
  browser.assert.cssProperty("#main", "display", "block");
  browser.assert.elementPresent("#main");
  browser.assert.elementNotPresent(".should_not_exist");
  browser.assert.hidden(".should_not_be_visible");
  browser.assert.title("Nightwatch.js");
  browser.assert.urlContains('google');
  browser.assert.urlEquals('http://www.google.com');
  browser.assert.value("form.login input[type=text]", "username");
  browser.assert.valueContains("form.login input[type=text]", "username");
  browser.assert.visible(".should_be_visible");
 
  //Commands
  browser.click("#main ul li a.first");
  browser.clearValue('input[type=text]');
  browser.closeWindow();
  browser.deleteCookie("test_cookie");
  browser.deleteCookies();
  browser.end();
  browser.getAttribute("#main ul li a.first", "href", function (result) {})
  browser.getCookie(name, function (result) {})
  browser.getCookies(function (result) {})
  browser.getCssProperty("#main ul li a.first", "display", function (result) {})
  browser.getElementSize("#main ul li a.first", function (result) {})
  browser.getLocation("#main ul li a.first", function (result) {})
  browser.getLocationInView("#main ul li a.first", function (result) {})
  this.getLog('browser', function (logEntriesArray) {})
  this.getLogTypes(function (typesArray) {})
  browser.getTagName("#main ul li .first", function (result) {})
  browser.getText("#main ul li a.first", function (result) {})
  browser.getTitle(function (title) {})
  browser.getValue("form.login input[type=text]", function (result) {})
  browser.init();
  this.injectScript("/path/to/script.js")
  browser.isLogAvailable('browser', function (isAvailable) {})
  browser.isVisible('#main', function (result) {})
  browser.maximizeWindow();
  browser.moveToElement('#main', 10, 10);
  browser.pause(1000);
  browser.perform(function (done) {})
  browser.resizeWindow(1000, 800);
  browser.saveScreenshot('/path/to/screenshot.png');
  browser.setCookie({
    name     : "test_cookie",
    value    : "test_value",
    path     : "/", //Optional
    domain   : "example.org", //Optional
    secure   : false, //Optional
    httpOnly : false, //Optional
    expiry   : 1395002765 //Optional, time in seconds since midnight, January 1, 1970 UTC
  });
  browser.setValue('input[type=text]', 'nightwatch');
  browser.setWindowPosition(0, 0);
  browser.submitForm('form.login');
  browser.switchWindow(handle);
  browser.urlHash('#hashvalue');
  browser.useCss()
  browser.useXpath()
  browser.waitForElementNotPresent('#dialog', 1000);
  browser.waitForElementNotVisible('#dialog', 1000);
  browser.waitForElementPresent('body', 1000);
  browser.waitForElementVisible('body', 1000);
};
```
