## Test avec selenium

### Selenium Javascript :

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


###Selenium tests :

    require('chromedriver');
    const chrome = require('selenium-webdriver/chrome');
    const {Builder, By, Key, until} = require('selenium-webdriver');

    process.env.NODE_ENV = 'test';

    jest.setTimeout(100000);

    describe('Seleniums test', () => {

      test('Home test', async () => {

        const driver = await new Builder()
          .forBrowser('chrome')
          //.setChromeOptions(new chrome.Options().headless())
          //.setChromeOptions(new chrome.Options().addArguments(['--headless', '--no-sandbox', '--disable-dev-shm-usage']))
          .setChromeOptions(new chrome.Options().addArguments(['--headless', '--no-sandbox', '--disable-dev-shm-usage']))
          .build();
          //.setChromeOptions(new chrome.Options().addArguments(['--headless','--no-sandbox', '--disable-dev-shm-usage']))
        try {
          //use localhost, node server, or pre-production adress
          await driver.get('http://localhost:3000/');
          expect(driver).not.toBeUndefined();

          // Enter text "cheese" and perform keyboard action "Enter"
          //await driver.findElement(By.name('q')).sendKeys('cheese', Key.ENTER);
          //const firstResult = await driver.wait(until.elementLocated(By.css('h3')), 10000);
          //console.log(await firstResult.getAttribute('textContent'));
        }
        finally{
          driver.quit();
        }
      });
    });


### TESTS PIPELINE GITLAB CI :

    #image: node:latest
    #image: node:latest
    #image: docker:latest

    stages:
      - build
      - test
      - deploy

    cache:
      paths:
        - node_modules/

    build:
      image: node:latest
      stage: build
      script:
        - npm install
        - npm install -g jest-cli
      artifacts:
        paths:
          - node_modules/

    unit_tests:
      image: node:latest
      stage: test
      script: npm test -- tests/App.test.js
      when: manual

    integration_test:
      image: debian:latest
      stage: test
      before_script:
          # install NPM
          - apt-get update
          #- apt-get remove google-chrome-stable >/dev/null
          - apt-get -y install curl dirmngr apt-transport-https lsb-release wget unzip libsqlite3-dev
          - curl -sL https://deb.nodesource.com/setup_11.x | bash -
          - apt-get -y install nodejs
          #- npm rebuild
          - npm install
          # install chrome
          - echo "deb http://dl.google.com/linux/chrome/deb/ stable main" | tee -a /etc/apt/sources.list
          #- cat gpgkey | apt-key add -
          - wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | apt-key add - >/dev/null
          - apt-get -qq update -y
          - apt-get -qq install -y google-chrome-stable xvfb gtk2-engines-pixbuf xfonts-cyrillic xfonts-100dpi xfonts-75dpi xfonts-base xfonts-scalable imagemagick x11-apps default-jre
          # use Xvbf for chromeZ
          - Xvfb :99 -ac -screen 0 1280x1024x24 &
          - export DISPLAY=:99
          #- npm install -g chromedriver --chromedriver-force-download
          #- nice -n 10 x11vnc 2>&1 &
      script:
          - npm run dev &
          - npm test -- tests/Selenium.test.js --host=selenium__standalone-chrome
      #allow_failure: false
      variables:
          SELENIUM_HOST: "selenium-standalone-chrome"
          #selenium_remote_url: "http://selenium__standalone-chrome:4444/wd/hub/"
      services:
          - name: selenium/standalone-chrome:latest
      when: manual

    deploy:
      image: node:latest
      stage: deploy
      script: npm run start
      when: manual
