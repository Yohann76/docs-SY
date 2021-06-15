##Test avec selenium

###Selenium Javascript :

package.json :
- "chromedriver": "^91.0.1",
- "selenium-webdriver": "3.6.0",


intégration avec jest :

import React from 'react';
import { rest } from 'msw';
import { setupServer } from 'msw/node';
import { mount, shallow } from 'enzyme';
import Adapter from '@wojtekmaj/enzyme-adapter-react-17';
//import {Builder, Buy, Key, util} from 'selenium-webdriver';
import { Browser, PageLoadStrategy } from 'selenium-webdriver/lib/capabilities';
import chrome from 'selenium-webdriver/chrome';
//require('geckodriver');
require('chromedriver');


const {Builder, By, Key, until} = require('selenium-webdriver');

jest.setTimeout(30000);

describe('Seleniums test', () => {

  test('Home test', async () => {

    const driver = await new Builder().forBrowser('chrome').build();
    try {
      // Navigate to Url
      await driver.get('https://www.google.com');

      // Enter text "cheese" and perform keyboard action "Enter"
      await driver.findElement(By.name('q')).sendKeys('cheese', Key.ENTER);

      const firstResult = await driver.wait(until.elementLocated(By.css('h3')), 10000);

      console.log(await firstResult.getAttribute('textContent'));
    }
    finally{
      driver.quit();
    }
    /*
    const wrapper = await Browser.get('https://www.selenium.dev/');
    expect(wrapper).not.toBeUndefined();
    */
    expect(0).toBe(0);
  });
});


###Selenium IDE (extension web) :
