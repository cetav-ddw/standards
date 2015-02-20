CSS-Coding-Standards
====================

Para reducir al mínimo la fricción de nuestro CSS, los desarrolladores del CETAV hemos llegado a un consenso acerca de nuestros estándares de codificación para:

* Formato del CSS.
* Arquitectura de nuestro CSS, incluyendo objetivos, errores a evitar y buenas prácticas.

Este es *a living document*, lo cual significa que el contenido cambiará tanto como sea necesario, nuestro objetivo es actualizar esto como evoluciona el conocimiento, las buenas prácticas y promover una mayor coherencia en nuestro propio CSS.

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

El código *feo* sienta un mal precedente, por el contrario, el código que se ve limpio se siente limpio. Queremos un ambiente agradable para trabajar, lo que fomenta en otros miembros del equipo mantener el nivel de limpieza que encontraron.

#### Anatomía de una regla:

```css
selector {
    propiedad: valor;
    [<--declaración--->]
}
[<--Regla o ruleset--->]
```

## Orden y especificidad
Las reglas se deben escribir de tal manera que, utilicemos la Cascada y la Herencia, y siempre tratar de que la Especificidad este a un nivel similar (en la medida de lo posible).

#### especificidad

* Escribir los bloques de reglas en un orden específico: reset, third party, elementos, patrones, objetos, componentes, etc **No** escribir las reglas segun el orden en que los elementos se muestran en la pagina.
* En la medida de lo posible, las reglas subsecuentes deben heredar, nunca sobreescribir.
* Evitar sobrecalificar selectores, esto incrementa la especificidad, limita la reutilizacion y son menos eficientes (mas trabajo para el browser)
* Evitar anidar innecesariamente.
* Evitar *encadenar* selectores.

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



