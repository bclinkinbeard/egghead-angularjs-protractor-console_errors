egghead-angularjs-protractor-console_errors
===========================================

Code for the egghead.io video Detecting Console Errors in Protractor Tests

```js
var IndexPage = require('./IndexPage');

describe('hello-protractor', function () {

  var page = new IndexPage();

  beforeEach(function() {
      page.get();
  });

  afterEach(function () {
    browser.manage().logs().get('browser').then(function (browserLog) {
      expect(browserLog.length).toEqual(0);
      if (browserLog.length) console.error('log: ' + JSON.stringify(browserLog));
    });
  });

  describe('index', function () {
    it('should display the correct title', function () {
      expect(page.getTitle()).toBe('hello protractor');
    });

    it('should display the message when button clicked', function () {
      page.clickButton();

      expect(page.getMessageText()).toBe('button 1 clicked');
    });
  });
});
```