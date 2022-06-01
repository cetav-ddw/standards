HTML-Coding-Standards
====================

Este documento define las reglas de formato y estilo para HTML. Su objetivo es mejorar la colaboración y la calidad del código.

## Sintaxis y formato

### Identación
* Idente usando 2 espacios a la vez.
* No utilice tabulaciones ni mezcle tabulaciones y espacios para identar.
* Idealmente se configura desde su editor de texto.

```html
<ul>
  <li>Fantastic</li>
  <li>Great</li>
</ul>
```

```css
selector {
  propiedad: valor;
}
```

### Capitalización
Use solo minúsculas.

Todo el código debe estar en minúsculas: esto se aplica a los nombres de elementos HTML, atributos, valores de atributos (a menos que sea texto/CDATA), selectores CSS, propiedades y valores de propiedad (con la excepción de las cadenas de texto).

```html
  <!-- No recomendado -->
  <A HREF="/">Inicio</A>

  <!-- Recomendado -->
  <a href="/">Inicio</a>
```

```css
/* No recomendado */
color: #E5E5E5;

/* Recomendado */
color: #e5e5e5;
```

### Encoding
Especifique la codificación de sus documentos HTML a través de `<meta charset="utf-8">`. No especifique la codificación de las hojas de estilo, ya que asumen UTF-8.