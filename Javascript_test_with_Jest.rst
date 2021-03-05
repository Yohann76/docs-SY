Jest ( Js testing ) 
--------

::

  npm install jest --save-dev

lancer les tests

::

  jest
  

les tests sont placé dans /tests/ et doivent avoir un nom en *.spec.js


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
