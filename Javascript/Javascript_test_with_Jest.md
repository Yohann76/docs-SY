###Jest ( Js testing ) 

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
  
  
  #### surcouche Enzyme
  
  pour les applications a rendu static comme jest, il y a parfois besoin d'une surcouche Enzyme :
  
  <pre>
    test('Testing Components : hamburger and menu', () => {
    const wrapper = mount(<Hamburger/>);
    const menuWrapper = shallow(<AnimatedMenu links={layout.navigation} />);

    expect(wrapper).not.toBeUndefined();
    expect(menuWrapper.find('#menu').getPropertyValue('display')).toBe('none');

    //expect(getComputedStyle(wrapper.getDOMNode()).getPropertyValue('display')).toBe('none');
    wrapper.simulate('click');
    expect(getComputedStyle(wrapper.getDOMNode()).getPropertyValue('display')).toBe('block');
  });
  </pre>
