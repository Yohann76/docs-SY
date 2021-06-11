Jest ( Js testing ) 
--------

::

  yarn add -D jest jest-cli

package.json script : 
::

  "test" : "jest --coverage"
  

lancer les tests 

::

  yarn test
  

fichier de test:

::

  function sum(a, b) {
    return a + b;
  }

  test('adds 1 + 2 to equal 3', () => {
    expect(sum(1, 2)).toBe(3);
  });

  test2('mon premier test', () => {
      expect(1).toBe(1);
  })
