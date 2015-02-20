CSS-Coding-Standards
====================

Para reducir al mínimo la fricción de nuestro CSS, los desarrolladores del CETAV hemos llegado a un consenso acerca de nuestros estándares de codificación para:

* Formato del CSS.
* Arquitectura de nuestro CSS, incluyendo objetivos, errores a evitar y buenas prácticas.

Este es *a living document*, lo cual significa que el contenido cambiará tanto como sea necesario, nuestro objetivo es actualizar esto como evoluciona el conocimiento, las buenas prácticas y promover una mayor coherencia en nuestro propio CSS.

## Agradecimientos

## Sintaxis y formato

Tener una forma estándar de escribir CSS significa que, el código siempre se verá y se sentirá familiar para todos los miembros del equipo.

El código feo sienta un mal precedente, por el contrario, el código que se ve limpio se siente limpio. Queremos un ambiente agradable para trabajar, lo que fomenta en otros miembros del equipo mantener el nivel de limpieza que encontraron.

## Uso de whitespace

### Indentación
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

### Espacios
Un espacio antes { (*bracket que abre*).

```css
/* Mal */
selector{

/* Bien */
selector {
```

Cierre en su su propia línea } (*bracket que cierra*).

```css
/* Mal */
selector{ }

/* Bien */
selector {
    
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



