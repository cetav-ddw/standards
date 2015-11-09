CSS-Coding-Standards
====================

Para reducir al mínimo la fricción de nuestro CSS, los desarrolladores del CETAV hemos llegado a un consenso acerca de nuestros estándares de codificación para:

* Formato del CSS.
* Arquitectura de nuestro CSS, incluyendo objetivos, errores a evitar y buenas prácticas.

Este es *a living document*, lo cual significa que, el contenido cambiará tanto como sea necesario, nuestro objetivo es actualizar este documento seg&uacute;n evoluciona el conocimiento y las buenas prácticas, tanto en clase como en la industria.

## Tabla de Contenidos

* [Agradecimientos](#agradecimientos)
* [Sintaxis y formato](#sintaxis-y-formato)
* [Orden y especificidad](#orden-y-especificidad)
* [Uso de whitespace](#uso-de-whitespace)
* [Comentarios](#comentarios)
* [Performance](#performance)

## Agradecimientos

## Sintaxis y formato
Tener una forma estándar de escribir CSS significa que, el código siempre se verá y se sentirá familiar para todos los miembros del equipo.

El código *feo* y desordenado sienta un mal precedente, por el contrario, el código que se ve limpio se siente limpio. Queremos un ambiente agradable para trabajar, lo que fomenta en otros miembros del equipo mantener el nivel de limpieza que encontraron.

A manera general queremos:

* Indentar con 4 espacios.
* Un espacio entre reglas.
* Un espacio antes del bracket de apertura (**{**), un espacio despues de dos puntos (**:**), punto y coma (**;**) y comas (**,**).
* Bracket de cierre (**}**) en su propia linea.
* Cada declaración en una linea.
* Ordenar alfabeticamente.
* Uso de minisculas y nombres en ingles.
* Cambio de palabra separado por un guion (**-**).

#### Anatom&iacute;a de una regla:

```css
selector {
    propiedad: valor;
    [<--declaración--->]
}
[<--Regla o ruleset--->]
```

### Convenciones para nombrar

#### Principios:

Cualquier nombre que se utiliza directamente en el HTML (class/id) deben tener en cuenta [estos principios](https://github.com/stubbornella/oocss/wiki/FAQ):

* *Claridad* - comportamiento esperado / estilo debe ser inmediatamente obvio.
* *Semántica* - lo que un objeto es importa más que como se ve.
* *Genérico* - el nombre debe ser aplicar para la mayoría de los sitios. Nombres demasiado específicos reducen el número de casos de uso o causa que clases semánticas sean utilizados en una forma no semántica.
* *Brevedad* - cada byte cuenta, así que mantenga nombres tan cortos como sea posible, pero siempre y cuando sea necesario. Nombres más de 5-7 caracteres deben ser abreviados.

Para separar palabras usamos gui&oacute;n en minuscula (*-*). Esto aplica para: clases, id, mixins, funciones, variables y colores:

```css
/* Mal */
.main_top { 
    color: #FFC20E; 
}

/* Bien */
.main-top { 
    color: #ffc20e; 
}
```

## Orden y especificidad
Las reglas se deben escribir de tal manera que, utilicemos la Cascada y la Herencia, y siempre tratar de que la Especificidad este a un nivel similar (en la medida de lo posible).

#### especificidad

* Escribir los bloques de reglas en un orden específico: reset, third party, elementos, patrones, objetos, componentes, etc **No** escribir las reglas seg&uacute;n el orden en que los elementos se muestran en la p&aacute;gina.
* En la medida de lo posible, las reglas subsecuentes deben heredar, nunca sobreescribir.
* Etiquetas - s&oacute;lo darle *estilo* a etiquetas globales.
* Clases - siempre es preferible darle *estilo* a selectores de tipo clase (.nombre-selector).
* IDs - evitar darle *estilo* a IDs. Incluso si el ID ya existe en la página, es mejor añadir una clase y darle *estilo*.
* Evitar sobrecalificar selectores, esto incrementa la especificidad, limita la reutilizacion y son menos eficientes (m&aacute;s trabajo para el browser)
* Evitar anidar innecesariamente.
* Evitar *encadenar* selectores. `.nav-item.expanded`

```css
/* Evitar sobrecalificar selectores */

/* Mal */
p.intro {

}

/* Bien */
.intro {

}
```

```css
/* Evitar anidar innecesariamente */

/* Mal */
.slide .panel-slide {

}

/* Bien */
.panel-slide {

}
```

```css
/* Evitar encadenar selectores */

/* Mal */
.message.error{

}

/* Bien */
.msj-error {

}
```

#### orden
Ordenar de forma alfanumérica, a excepción de donde se puede romper la Cascada.

* En la hoja de estilos: pseudo-selectores (:after, :active, :before, :hover, :link, :visited), etiquetas antes que clases y antes que ids - orden natual de la especificidad.
* Reglas, propiedades y selectores se deben ordenar alfabeticamente.

**Etiquetas y clases:**
```css
/* Mal */
.product-list {

}

p {
    
}

ul {
    
}

/* Bien */
p {
    
}

ul {
    
}

.product-list {

}
```

**Propiedades:**
```css
/* Mal */
selector {
    font-family: Arial, sans-serif; 
    padding: 0; 
    margin: 0; 
    color: red;
}

/* Bien */
selector {
    color: red; 
    font-family: Arial, sans-serif; 
    margin: 0; 
    padding: 0;
}
```

**Reglas:**
```css
/* Mal */
.product-list-thumb {

}

.product-list-item {

}

/* Bien */
.product-list-item {

}

.product-list-thumb {

}
```

## Uso de whitespace

#### indentación
Indentamos con **4 espacios**. Puede configurar su editor para que lo realice de manera automática.

```css
/* Mal */
selector {
  propiedad: valor;
}

/* Bien */
selector {
    propiedad: valor;
}
```

#### espacios
Una declaración (propiedad y valor) por línea.

```css
/* Mal */
selector {
    propiedad: valor; propiedad: valor; propiedad: valor;
}

/* Bien */
selector {
    propiedad: valor;
    propiedad: valor;
    propiedad: valor;
}
```

Un espacio antes **{** (*bracket que abre*).

```css
/* Mal */
selector{

/* Bien */
selector {
```

Cierre en su su propia línea **}** (*bracket que cierra*).

```css
/* Mal */
selector { }

/* Bien */
selector {
    
}
```

Espacio después de **:** (dos puntos), **;** (punto y coma) y **,** (comas).

```css
/* Mal */
selector {
    color:red;font-family:Helvetica,Arial,sans-serif;
}

/* Bien */
selector {
    color: red; font-family: Helvetica, Arial, sans-serif;
}
```


#### nueva línea
Después de cada regla incluimos nueva línea

```css
/* Mal */
selector {
    propiedad: valor; 
}
selector {
    propiedad: valor;
}

/* Bien */
selector {
    propiedad: valor;
}

selector {
    propiedad: valor;
}
```

Cuando hay bloques anidados, solo incluimos nueva línea antes del primer bloque

```css
/* Mal */
selector {
    propiedad: valor;

    selector {
        propiedad: valor;
    }

    selector {
        propiedad: valor;
    }

    selector {
        propiedad: valor;
    }
}

/* Bien */
selector {
    propiedad: valor;

    selector {
        propiedad: valor;
    }
    selector {
        propiedad: valor;
    }
    selector {
        propiedad: valor;
    }
}
```

Cuando agrupamos selectores, cada selector en su propia línea

```css
/* Mal */
selector, selector2, selector3 {
    propiedad: valor; 
}

/* Bien */
selector,
selector2,
selector3 {
    propiedad: valor;
}
```

#### strings comillas dobles (" ")

```css
/* Mal */
selector {
    font-family: 'Goudy Bookletter 1911', sans-serif;
}

/* Bien */
selector {
    font-family: "Goudy Bookletter 1911", sans-serif;
}
```

## Comentarios

## Performance
