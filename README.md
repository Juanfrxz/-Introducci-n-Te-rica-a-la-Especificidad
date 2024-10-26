- **Introducción Teórica a la Especificidad**
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
