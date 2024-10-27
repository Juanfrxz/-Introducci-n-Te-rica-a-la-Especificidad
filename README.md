- # **Parte 1: Introducción Teórica a la Especificidad**
  - **¿Qué es la especificidad?**
    - En HTML y CSS, la especificidad es un concepto clave en el diseño web que define qué reglas de estilo se aplican a un elemento en caso de conflicto. La especificidad ayuda a determinar qué estilos prevalecen cuando hay múltiples reglas CSS aplicables a un     
      mismo elemento. La especificidad se basa en el tipo de selectores utilizados y sigue una jerarquía. Cada tipo de selector tiene un "peso" que define su prioridad:
      - Selectores de ID (`#mi-id`): Tienen la especificidad más alta.
      - Selectores de clase, atributos y pseudoclases (`.mi-clase`, `[atributo=valor]`, `:hover`): Tienen una especificidad media.
      - Selectores de elementos (`h1`, `p`, `div`): Tienen la especificidad más baja.
      - Selectores universales y combinadores (`*`, `+`, `>`, `~`): No afectan la especificidad de forma directa.
  - **Reglas de cálculo de especificidad:**
    - En CSS, cada tipo de selector tiene un puntaje que determina su especificidad. Este puntaje se utiliza para calcular qué estilos se aplicarán a un elemento cuando haya reglas en conflicto. La especificidad se mide de la siguiente manera:
      - Selectores de ID: se asignan 100 puntos por cada selector de ID (`#mi-id`).
      - Selectores de clase, atributos y pseudoclases: cada uno recibe 10 puntos (`.mi-clase`, `[tipo="texto"]`, `:hover`).
      - Selectores de elementos y pseudoelementos: cada uno aporta 1 punto (`h1`, `p`, `::before`).
      La especificidad se suma en función de estos valores, y la regla con el puntaje más alto se aplica en caso de conflicto.
      `!important` y la cascada
      Cuando una regla utiliza `!important`, sobrescribe cualquier otra regla sin importar su especificidad, rompiendo la jerarquía de prioridades en la cascada de CSS. Sin embargo, si varias reglas `!important` están en conflicto, el navegador selecciona la que 
      tenga mayor especificidad.


          | Tipo de Selector                          | Ejemplo                   | Puntaje de Especificidad |
          |-------------------------------------------|---------------------------|--------------------------|
          | Estilos en línea (atributo `style`)       | `style="color: red;"`     | 1000                     |
          | Selector de ID                            | `#mi-id`                  | 100                      |
          | Selector de Clase                         | `.mi-clase`               | 10                       |
          | Selector de Atributo                      | `[type="text"]`           | 10                       |
          | Pseudoclase                               | `:hover`, `:first-child`  | 10                       |
          | Selector de Elemento                      | `p`, `div`, `span`        | 1                        |
          | Pseudoelemento                            | `::before`, `::after`     | 1                        |
          | Selector Universal                        | `*`                       | 0                        |
          | Combinadores                              | `>`, `+`, `~`             | 0                        |
          | `!important`                              | `color: red !important;`  | Sobrescribe especificidad |


- Los selectores universales (`*`), combinadores (`+`, `>`, `~`) y las pseudoclases negadas (`:not()`) **no afectan la especificidad**.
- El marcador `!important` sobrescribe otras reglas sin importar la especificidad.

> **Importante:** [Descargar presentación](https://github.com/user-attachments/files/17532713/Especificidad.CSS.y.HTML.pptx)


# **Parte 2: Ejemplos Prácticos**

![image](https://github.com/user-attachments/assets/343c5d4d-1d19-42f8-9847-d35313824b6c)


El texto del párrafo `Hola Mundo` aparecerá en rojo porque el selector de ID `#parrafo` tiene una especificidad más alta (100 puntos), superando tanto el selector de clase como el de tipo.

![image](https://github.com/user-attachments/assets/24b867a9-8ce9-47d2-bf14-9ee6516482e3)

El texto "Hola Mundo" se mostrará en azul porque `!important` en el selector `p` hace que esa regla se aplique sobre cualquier otra.

# **Parte 3: Ejercicios Prácticos**

Distribuye a los participantes los siguientes ejercicios para que los realicen por su cuenta o en
grupos pequeños:

Ejercicio 1: Calculando la Especificidad

![alt text](https://github.com/user-attachments/assets/145fa109-dc5a-4f86-8fd8-49219c4d4b9d)


El color del título `<h1>` será rojo, ya que el selector de ID `#main h1` tiene la mayor especificidad con 101 puntos, superando al selector de clase y al selector de tipo.

Ejercicio 2: Resolviendo Conflictos de Especificidad

![alt text](https://github.com/user-attachments/assets/57fdd73b-f1bb-4101-a287-b293528d6cfe)


Explicación: Este nuevo selector `#box .text` tiene una especificidad de `100 (ID) + 10 (clase) = 110` puntos, lo que supera a las otras reglas y hace que el color del párrafo sea amarillo, sin necesidad de usar `!important`.

# **Parte 4: Desafío Final**

Desafío: Diseñando una Página Completa con Estilos Conflictivos

Dales a los participantes un archivo HTML con múltiples elementos y clases, y pídeles que
agreguen estilos CSS para lograr un diseño específico. Deberán aplicar todo lo aprendido sobre
especificidad para resolver los conflictos y obtener el resultado correcto.

```html
<div class="header" id="top">
<h1>Bienvenido</h1>
  <p id="intro">Este es el sitio web.</p>
</div>
<div class="content">
  <h2>Contenido principal</h2>
  <p class="highlight">Texto destacado</p>
</div>
<footer id="footer">
  <p>Pie de página</p>
</footer>
```

![alt text](https://github.com/user-attachments/assets/a0e41c9e-a479-4bdb-866d-899b7f66b405)

Esta estructura aprovecha la especificidad sin necesidad de `!important`, aplicando los estilos de forma precisa en los elementos requeridos.
