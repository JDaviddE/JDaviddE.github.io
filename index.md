---
layout: default
---

Text can be **bold**, _italic_, or ~~strikethrough~~.

[Link to another page](./another-page.html).

There should be whitespace between paragraphs.

There should be whitespace between paragraphs. We recommend including a README, or a file with information about your project.

# Programación funcional en Python
## ¿Que es?
La programación funcional (PF) es un paradigma de programación al igual que la programación orientada a objetos (POO). La PF se basa en cálculo lambda y concretamente en composición de funciones puras para modelar las soluciones de software.
La programación funcional es un paradigma declarativo. Nos enfocaremos en "qué" estamos haciendo y no en "cómo" se está haciendo que sería el enfoque imperativo. Esto quiere decir que nosotros expresaremos nuestra lógica sin describir controles de flujo; no usaremos ciclos o condicionales.

### Funciones de primera clase
Todo lo que se puede hacer con “datos” se puede hacer con las funciones mismas.
>Tratar funciones como objetos permite la composición y abstracción de código de manera eficaz.

```js
def cuadrado(x):
    return x ** 2
funcion = cuadrado
print(funcion(5))  
```
### Recursividad
Sirve para resolver problemas dividiéndolos en subproblemas más pequeños y manejables.
Una función puede realizar un llamado a sí misma durante su ejecución.
```js
def suma_naturales(n):
    if n == 0:
        return 0
    else:
        return n + suma_naturales(n - 1)
```
La idea básica es dividir el problema en partes más pequeñas y aplicar la misma operación de suma a esas partes más pequeñas hasta llegar al resultado.
### Funciones lambda

Las funciones lambda son funciones anónimas y simples, convenientes para operaciones rápidas sin necesidad de definición formal.
Son más breves y se pueden definir en una sola línea de código.
Útiles para operaciones simples y rápidas sin la necesidad de una definición formal. 
Se utilizan comúnmente como argumentos en funciones como map, filter, reduce.

### Funciones de alto orden
Son aquellas funciones que pueden recibir otras funciones como parámetro y/o devolver funciones como resultado.
Permite construir operaciones complejas a partir de funciones más simples.

* Map: Aplica una función a cada elemento de un iterable ej: una lista y devuelve un nuevo iterable con los resultado.
   
```js
def convertirAAnios(x):
    return {
        x["nombre"].lower(),
        x["Edad"]/12,
        x["Vegetariano"]
    }
listaEstudiantes = [ 
    {"nombre":"Diego","Edad":552,"Vegetariano":False},
    {"nombre":"Diana","Edad":480,"Vegetariano":False},
    {"nombre":"Camila","Edad":312,"Vegetariano":True}
]

listaEdadAnios = list(map(convertirAAnios,listaEstudiantes))
print(listaEdadAnios)
```
* Filter:Filtra los elementos de un iterable según una función que retorna valores booleanos.
  
```js
def filtrarVegetarianos(x):
    x["Vegetariano"] = True

listaEstudiantes = [ 
    {"nombre":"Diego","Edad":552,"Vegetariano":False},
    {"nombre":"Diana","Edad":480,"Vegetariano":False},
    {"nombre":"Camila","Edad":312,"Vegetariano":True}
]
listaVegetarianos = list(filter(lambda x:x["Vegetariano"]==True,listaEstudiantes))
listaEdadAnios = list(map(convertirAAnios,listaVegetarianos))
print(listaEdadAnios)
```
* Reduce: Aplica una función a una secuencia de dos elementos, luego al resultado y al siguiente elemento, devuelve un solo valor.
  
```python
from functools import reduce

# Generación de la lista de enteros de prueba desde 2 hasta 100, 
# con incrementos de 2
listaNumerosPares = list(range(2, 101, 2))
print(listaNumerosPares)

# Cálculo de una sumatoria usando un iterador:
suma_iterador = 0
for i in listaNumerosPares:
    suma_iterador += i

print(suma_iterador)

# Serie sumatoria, usando la función reduce con función predefinida
def MiSuma(x, y):
    return x + y

# Reduce usando la función suma predefinida
sumaTotalReduce1 = reduce(MiSuma, listaNumerosPares)

# Reduce usando una función lambda para la suma
sumaTotalReduce2 = reduce(lambda x, y: x + y, listaNumerosPares)

# Otra función lambda de reducción (división)
productoTotalReduce = reduce(lambda x, y: x / y, listaNumerosPares)


print(f"Suma con reduce (MiSuma): {sumaTotalReduce1}")
print(f"Suma con reduce (lambda): {sumaTotalReduce2}")
print(f"Producto con reduce (lambda): {productoTotalReduce}")
```

Y aqui otro ejemplo de reduce pero con concatenación

```python
# Una lista de cadenas, para usar otra función de "reducción" (concatenación)
listaCadenas = ["Muchos", "años", "después", ",", "frente", "al", "pelotón", "de", "fusilamiento"]
# Reducción con concatenación
inicioCienAniosSOledad = reduce(lambda x, y: x + " " + y, listaCadenas)
print(inicioCienAniosSOledad)
```

* * *

# Programación Orientada a objetos en Python
La programación orientada a objetos (POO) es un paradigma de programación que se basa en el concepto de "objetos", los cuales pueden contener datos en forma de campos (también conocidos como atributos) y código, en forma de procedimientos (también conocidos como métodos)

## Conceptos de OOP
1- Abstracción, es la capacidad de definir objetos que representan conceptos abstractos o entidades del mundo real y los comportamientos asociados con ellos.

2- Encapsulamiento, consiste en ocultar los detalles internos de un objeto y exponer solo lo que es necesario.



### Header 3

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
