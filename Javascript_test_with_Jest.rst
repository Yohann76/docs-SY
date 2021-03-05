Jest ( Js testing ) 
--------

::

  npm install jest --save-dev

lancer les tests

::

  jest
  

une fonction:

::

  const {theTruth} = require('./index')
  describe('ma première suite de tests', () => {
    test('mon premier test', () => {
      const isTrue = theTruth()
      expect(isTrue).toBe(true)
    })
  })
