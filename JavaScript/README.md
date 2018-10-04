JavaScript Coding Standards
===========================

## <a name='TOC'>Tabla de Contenido</a>
  
  1. [Puntuación](#puntuacion)
  1. [Tipos](#types)
  1. [Objetos](#objects)
  1. [Arreglos](#arrays)
  1. [Cadenas de Texto](#strings)
  1. [Funciones](#functions)
  1. [Propiedades](#properties)
  1. [Variables](#variables)
  1. [Hoisting](#hoisting)
  1. [Expresiones de comparación e igualdad](#conditionals)
  1. [Comentarios](#comments)
  1. [Casting de Tipos & Coerción](#type-coercion)
  1. [Funciones de Acceso](#accessors)
  1. [Constructores](#constructors)
  1. [Eventos](#events)
  1. [Módulos](#modules)
  1. [Recursos](#resources)
  1. [Licencia](#license)

[Basado en Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)

## Sintaxis y formato

A manera general queremos:

* Utilizamos ECMAScript 6.0 (ES6) - [ECMAScript® 2015 Language Specification](https://www.ecma-international.org/ecma-262/6.0/index.html)
* Indentar con **2** espacios, no tabs.
* Deja un espacio antes de la llave de apertura `{`.
* Usar llaves con todos los bloques de múltiples líneas (```if``` , ```function```).
* Un espacio antes del paréntesis de apertura en las sentencias de control (```if```, ```while```, etc.).
* Bloques de muchas líneas con ```if``` y ```else```, poner el ```else``` en la misma línea que el ```if```.
* No espacio entre el keyword function o el nombre de la funcion y el primer parentesis (`function() {}`)
* Separar a los operadores con espacios. `const x = y + 5;`
* Deja una línea en blanco luego de los bloques y antes de la siguiente sentencia.
* Ser descriptivo con nombres de variables, métodos, funciones, etc.
* camelCase para nombrar objetos, funciones e instancias, ejem: `thisIsMyObject`, `thisIsMyFunction`
* PascalCase cuando nombre constructores o clases.
* No usar [palabras reservadas](https://www.ecma-international.org/ecma-262/6.0/index.html#sec-reserved-words) para nombres de propiedades, funciones o variables.
* Nombre sus funciones. Esto será de ayuda en caso de errores.

## <a name='puntuacion'>Puntuación: comas, puntos y coma</a>

  - **No** usar comas al inicio de línea:

    ```javascript
    // mal
    const story = [
        once
      , upon
      , aTime
    ];

    // bien
    const story = [
      once,
      upon,
      aTime
    ];
    ```

  - **Sip.**

    ```javascript
    // mal
    (function() {
      const name = 'Skywalker'
      return name
    })()

    // bien
    (function() {
      const name = 'Skywalker';
      return name;
    })();
    ```

## <a name='types'>Tipos</a>

  - **Primitivos**: Cuando accesas a un tipo primitivo, manejas directamente su valor

    + `string`
    + `number`
    + `boolean`
    + `null`
    + `undefined`


    ```javascript
    let foo = 1;
    let bar = foo;

    let = 9;

    console.log(foo, bar); // => 1, 9
    ```
  - **Complejo**: Cuando accesas a un tipo complejo, manejas la referencia a su valor.

    + `object`
    + `array`
    + `function`


    ```javascript
    var foo = [1, 2];
    var bar = foo;

    bar[0] = 9;

    console.log(foo[0], bar[0]); // => 9, 9
    ```

    **[[⬆ regresar a la Tabla de Contenido]](#TOC)**

## <a name='objects'>Objetos</a>

  - Usa la sintaxis literal para la creación de un objeto.


    ```javascript
    // mal
    var item = new Object();

    // bien
    var item = {};
    ```

    **[[⬆ regresar a la Tabla de Contenido]](#TOC)**

## <a name='arrays'>Arreglos</a>

  - Usa la sintaxis literal para la creación de arreglos

    ```javascript
    // mal
    var items = new Array();

    // bien
    var items = [];
    ```

  - Usa Array#push, en vez de asignación directa, para agregar elementos a un arreglo.

    ```javascript
    var someStack = [];

    // mal
    someStack[someStack.length] = 'abracadabra';

    // bien
    someStack.push('abracadabra');
    ```

  - Cuando necesites copiar un arreglo usa Array#slice. [jsPerf](http://jsperf.com/converting-arguments-to-an-array/7)

    ```javascript
    var len = items.length;
    var itemsCopy = [];
    var i;

    // mal
    for (i = 0; i < len; i++) {
      itemsCopy[i] = items[i];
    }

    // bien
    itemsCopy = items.slice();
    ```

    **[[⬆ regresar a la Tabla de Contenido]](#TOC)**


## <a name='strings'>Cadenas de Texto</a>

  - Usa comillas simples `''` para las cadenas de texto

    ```javascript
    // mal
    var name = "Bob Parr";

    // bien
    var name = 'Bob Parr';

    // mal
    var fullName = "Bob " + this.lastName;

    // bien
    var fullName = 'Bob ' + this.lastName;
    ```

  - Cuando se crea programáticamente una cadena de texto, use _template strings_ (``) en vez de

    ```javascript
    // mal
    function sayHi(name) {
      return 'How are you, ' + name + '?';
    }

    // mal
    function sayHi(name) {
      return ['How are you, ', name, '?'].join();
    }

    // mal
    function sayHi(name) {
      return `How are you, ${ name }?`;
    }

    // bien
    function sayHi(name) {
      return `How are you, ${name}?`;
    }
    ```

    **[[⬆ regresar a la Tabla de Contenido]](#TOC)**


## <a name='functions'>Funciones</a>

  - Expresiones de función:

    ```javascript
    // expresion de funcion anonima
    const anonymous = function() {
      return true;
    };

    // expresion de funcion nombrada
    const named = function named() {
      return true;
    };

    // expresion de funcion inmediatamente invocada (IIFE)
    (function() {
      console.log('Welcome to the Internet. Please follow me.');
    })();
    ```

  - Nunca declare una función en un bloque que no sea de función (if, while, etc). En vez de ello, asigna la función a una variable. Los navegadores te permitirán hacerlo pero todos ellos lo interpretarán de modo diferente, lo que es lamentable.

  - Nunca nombres a un parámetro como `arguments`, esto tendrá precedencia sobre el objeto `arguments` que es brindado en cada ámbito de función.

    **[[⬆ regresar a la Tabla de Contenido]](#TOC)**


## <a name='properties'>Propiedades</a>

  - Usa la notación de punto `.` cuando accedas a las propiedades.

    ```javascript
    const luke = {
      jedi: true,
      age: 28
    };

    // mal
    const isJedi = luke['jedi'];

    // bien
    const isJedi = luke.jedi;
    ```

  - Usa la notación subscript `[]` cuando accedas a las propiedades con una variable.

    ```javascript
    const luke = {
      jedi: true,
      age: 28
    };

    function getProp(prop) {
      return luke[prop];
    }

    const isJedi = getProp('jedi');
    ```

    **[[⬆ regresar a la Tabla de Contenido]](#TOC)**


## <a name='variables'>Variables</a>

  - Siempre usar `const` o `let` para declarar variables. No hacerlo resultará en variables globales. Debemos evitar contaminar el espacio global (global namespace).

  - Usar una declaración `const` o `let` por variable.

    ```javascript
    const items = getItems();
    const goSportsTeam = true;
    const dragonball = 'z';
    ```

  - Agrupe todas sus declaraciones `const` y luego las declaraciones `let`.

  - Declarar a las variables sin asignación al final. Esto es útil cuando necesites asignar una variable luego dependiendo de una de las variables asignadas previamente.

    ```javascript
    let items = getItems();
    let goSportsTeam = true;
    let dragonball;
    let length;
    let i;
    ```

  - Asigna las variables al inicio de su ámbito. Esto ayuda a evitar inconvenientes con la declaración de variables y temas relacionados a 'hoisting'.

    ```javascript
    // mal
    function() {
      test();
      console.log('doing stuff..');

      //..otras cosas..

      let name = getName();

      if (name === 'test') {
        return false;
      }

      return name;
    }

    // bien
    function() {
      let name = getName();

      test();
      console.log('doing stuff..');

      //..otras cosas..

      if (name === 'test') {
        return false;
      }

      return name;
    }

    // mal - llamada a funcion innecesaria
    function() {
      let name = getName();

      if (!arguments.length) {
        return false;
      }

      this.setFirstName(name);

      return true;
    }

    // bien
    function() {
      if (!arguments.length) {
        return false;
      }

      let name = getName();
      this.setFirstName(name);

      return true;
    }
    ```

    **[[⬆ regresar a la Tabla de Contenido]](#TOC)**


## <a name='hoisting'>Hoisting</a>

  **POR ACTUALIZAR**

  - Las declaraciones de variables son movidas a la parte superior de su ámbito, sin embargo su asignación no.

    ```javascript
    // sabemos que esto no funcionara (asumiendo
    // que no hay una variable global notDefined)
    function example() {
      console.log(notDefined); // => lanza un ReferenceError
    }

    // crear una declaracion de variable luego
    // que referencies a la variable funcionara
    // por el hoisting. Nota: A la asignacion
    // del valor `true` no se le aplico hoisting.
    function example() {
      console.log(declaredButNotAssigned); // => undefined
      var declaredButNotAssigned = true;
    }

    // El interprete lleva la declaracion de la
    // variable a la parte superior de la funcion.
    // Eso significa que nuestro ejemplo
    // podria ser reescrito como:
    function example() {
      var declaredButNotAssigned;
      console.log(declaredButNotAssigned); // => undefined
      declaredButNotAssigned = true;
    }
    ```

  - Expresiones de función anónimas hacen hoisting de su nombre de variable, pero no de la asignación de la función.

    ```javascript
    function example() {
      console.log(anonymous); // => undefined

      anonymous(); // => TypeError anonymous is not a function

      var anonymous = function() {
        console.log('anonymous function expression');
      };
    }
    ```

  - Expresiones de función nombradas hacen hoisting de su nombre de variable, pero no del nombre de la función ni del contenido de la función.

    ```javascript
    function example() {
      console.log(named); // => undefined

      named(); // => TypeError named is not a function

      superPower(); // => ReferenceError superPower is not defined

      var named = function superPower() {
        console.log('Flying');
      };
    }

    // lo mismo es cierto cuando el nombre
    // de la funcion es igual al nombre de
    // la variable.
    function example() {
      console.log(named); // => undefined

      named(); // => TypeError named is not a function

      var named = function named() {
        console.log('named');
      }
    }
    ```

  - Las declaraciones de función hacen hoist de su nombre y del contenido de la función.

    ```javascript
    function example() {
      superPower(); // => Flying

      function superPower() {
        console.log('Flying');
      }
    }
    ```

    **[[⬆ regresar a la Tabla de Contenido]](#TOC)**


## <a name='conditionals'>Expresiones de comparación e igualdad</a>

  - Usa `===` y `!==` en vez de `==` y `!=` respectivamente.
  - Expresiones condicionales son evaluadas usando coerción con el método `ToBoolean` y siempre obedecen a estas reglas sencillas:

    + **Objects** son evaluados como **true** (también considera así al objeto vacío ```{}``` y arreglos sin contenido ```[]```)
    + **Undefined** es evaluado como **false**
    + **Null** es evaluado como **false**
    + **Booleans** son evaluados como **el valor del booleano**
    + **Numbers** son evaluados como **false** si **+0**, **-0**, o **NaN**, de otro modo **true**
    + **Strings** son evaluados como **false** si es una cadena de texto vacía `''`, de otro modo son **true**

    ```javascript
    if ([0]) {
      // true
      // un arreglo es un objeto, los objetos son evaluados como true
    }
    ```

  - Usa atajos.

    ```javascript
    // mal
    if (name !== '') {
      // ...stuff...
    }

    // bien
    if (name) {
      // ...stuff...
    }

    // mal
    if (collection.length > 0) {
      // ...stuff...
    }

    // bien
    if (collection.length) {
      // ...stuff...
    }
    ```

    **[[⬆ regresar a la Tabla de Contenido]](#TOC)**


## <a name='comments'>Comentarios</a>

  - Usa `/** ... */` para comentarios de múltiples líneas. Incluye una descripción, especificación de tipos y valores para todos los parámetros y valores de retorno.

    ```javascript
    /**
     * make() returns a new element
     * based on the passed in tag name
     *
     * @param {String} tag
     * @return {Element} element
     */
    function make(tag) {

      // ...stuff...

      return element;
    }
    ```

  - Usa `//` para comentarios de una sola línea. Ubica los comentarios de una sola línea encima de la sentencia comentada. Deja una línea en blanco antes del comentario.

    ```javascript
    function getType() {
      console.log('fetching type...');

      // set the default type to 'no type'
      const type = this._type || 'no type';

      return type;
    }
    ```

    **[[⬆ regresar a la Tabla de Contenido]](#TOC)**


## <a name='type-coercion'>Casting de Tipos & Coerción</a>

  - Ejecuta coerción al inicio de una sentencia.
  - Strings:

    ```javascript
    // => this.reviewScore = 9;

    // mal
    const totalScore = new String(this.reviewScore);

    // mal
    const totalScore = this.reviewScore + '';

    // mal
    const totalScore = this.reviewScore.toString();

    // bien
    const totalScore = String(this.reviewScore);
    ```

  - Usa `parseInt` para números y siempre con la base numérica para el casting de tipo.

    ```javascript
    const inputValue = '4';

    // mal
    const val = new Number(inputValue);

    // mal
    const val = +inputValue;

    // mal
    const val = inputValue >> 0;

    // mal
    const val = parseInt(inputValue);

    // bien
    const val = Number(inputValue);

    // bien
    const val = parseInt(inputValue, 10);
    ```

  - Booleans:

    ```javascript
    const age = 0;

    // mal
    const hasAge = new Boolean(age);

    // bien
    const hasAge = Boolean(age);

    // mejor
    const hasAge = !!age;
    ```

    **[[⬆ regresar a la Tabla de Contenido]](#TOC)**

## <a name='accessors'>Funciones de Acceso</a>

  **POR ACTUALIZAR**

  - Funciones de acceso para las propiedades no son requeridas, pero si se crean, usar  ```getVal()``` y ```setVal('hello')```. Ejem: `getAge()`, `setAge(25)`.

  - Si la propiedad es un booleano, usa ```isVal()``` o ```hasVal()```.

    **[[⬆ regresar a la Tabla de Contenido]](#TOC)**


## <a name='constructors'>Constructores</a>

  **POR ACTUALIZAR**

  - Asigna métodos al objeto prototype, en vez de sobreescribir prototype con un nuevo objeto. La sobreescritura de prototype hace la herencia imposible: ¡reseteando prototype sobreescribirás la base!

  - Métodos pueden retornar `this` para ayudar con el encadenamiento de métodos (chaining).

    ```javascript
    // mal
    Jedi.prototype.jump = function() {
      this.jumping = true;
      return true;
    };

    Jedi.prototype.setHeight = function(height) {
      this.height = height;
    };

    var luke = new Jedi();
    luke.jump(); // => true
    luke.setHeight(20) // => undefined

    // bien
    Jedi.prototype.jump = function() {
      this.jumping = true;
      return this;
    };

    Jedi.prototype.setHeight = function(height) {
      this.height = height;
      return this;
    };

    var luke = new Jedi();

    luke.jump()
      .setHeight(20);
    ```

    **[[⬆ regresar a la Tabla de Contenido]](#TOC)**


## <a name='events'>Eventos</a>

  **POR ACTUALIZAR**

  - Cuando envíes paquetes de datos a los eventos (ya sea con eventos del DOM o algo propietario como los eventos de Backbone), pasa un mapa en vez de un valor directo. Esto permitirá a un próximo colaborador a agregar más datos al paquete de datos sin que tenga que encontrar o actualizar un handler para cada evento. Por ejemplo, en vez de:

    ```js
    // mal
    $(this).trigger('listingUpdated', listing.id);

    ...

    $(this).on('listingUpdated', function(e, listingId) {
      // hacer algo con listingId
    });
    ```

    prefiere:

    ```js
    // bien
    $(this).trigger('listingUpdated', { listingId : listing.id });

    ...

    $(this).on('listingUpdated', function(e, data) {
      // hacer algo con data.listingId
    });
    ```

  **[[⬆ regresar a la Tabla de Contenido]](#TOC)**


## <a name='modules'>Módulos</a>

  **POR ACTUALIZAR**

  - El módulo debe empezar con un `!`. Esto asegura que si un módulo mal formado olvide incluir al final un punto y coma, no hayan errores en producción cuando los scripts sean concatenados. [Explicación](https://github.com/airbnb/javascript/issues/44#issuecomment-13063933)
  - El archivo debe ser nombrado con camelCase, residir en un fólder con el mismo nombre, y corresponder al nombre de la función a exportar.
  - Agrega un método `noConflict()` que reestablezca el módulo exportado a la versión anterior y retorne este módulo (para ser asignado a una variable).
  - Siempre declara `'use strict';` al inicio de cada módulo.

    ```javascript
    // fancyInput/fancyInput.js

    !function(global) {
      'use strict';

      var previousFancyInput = global.FancyInput;

      function FancyInput(options) {
        this.options = options || {};
      }

      FancyInput.noConflict = function noConflict() {
        global.FancyInput = previousFancyInput;
        return FancyInput;
      };

      global.FancyInput = FancyInput;
    }(this);
    ```

    **[[⬆ regresar a la Tabla de Contenido]](#TOC)**


## <a name='recursos'>Recursos</a>
  
  - [JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
  - [Truth Equality and JavaScript](http://javascriptweblog.wordpress.com/2011/02/07/truth-equality-and-javascript/#more-2108)
  - [JavaScript Scoping & Hoisting](http://www.adequatelygood.com/2010/2/JavaScript-Scoping-and-Hoisting)
  - [Google JavaScript Style Guide](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml) (Guía de Estilo de Javascript de Google)
  - [jQuery Core Style Guidelines](http://docs.jquery.com/JQuery_Core_Style_Guidelines) (Lineamientos de Estilo con el núcleo de jQuery)
  - [Principles of Writing Consistent, Idiomatic JavaScript](https://github.com/rwldrn/idiomatic.js/) (Idiomatic Javascript: Principios de Escritura Consistente)
  - [JavaScript Standard Style](https://github.com/feross/standard) (Estilo estándar de JavaScript)
  - [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript/tree/es5-deprecated/es5)


## <a name='license'>Licencia</a>

(The MIT License)

Copyright (c) 2012 Airbnb

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

**[[⬆ regresar a la Tabla de Contenido]](#TOC)**

# };
