# Tipos de datos, variables, literales y constantes

## Tipos de datos

### ¿Qué es un tipo de dato?

> “Todos los valores posibles que una variable de ese tipo de dato puede tomar”
>
> — Mariano Méndez

Un **tipo de dato** define qué clase de información puede almacenar una variable, no es lo mismo guardar un número entero que una letra o un valor verdadero/falso. Cada tipo establece un rango de valores válidos y las operaciones que se pueden hacer con ellos.

Por ejemplo, el tipo entero incluye valores como `-5`, `0`, `1`, `42`, pero no incluye `3.14` ni `"hola"`. El tipo carácter incluye letras como `'A'` o `'z'`, pero no números reales.

---

### Python vs C

En **Python**, no es necesario declarar el tipo de dato de una variable ya que el intérprete lo infiere automáticamente según el valor que se le asigna.

Esto se llama **tipado dinámico**.

``` python
x = 5          # Python infiere que x es un entero
y = 3.14       # Python infiere que y es un flotante
nombre = "Ana" # Python infiere que nombre es una cadena
activo = True  # Python infiere que activo es booleano
```

En **C**, en cambio, es obligatorio declarar el tipo de cada variable antes de usarla.

Esto se llama **tipado estático**, una variable solo puede contener valores del tipo con el que fue declarada, durante toda la ejecución del programa.

``` c
int x = 5;
double y = 3.14;
char inicial = 'A';
bool activo = true;
```

---

### Tipos de dato en C

To-do: preguntar si debería poner rangos

<center>

| Tipos genéricos | Tipos de dato en C |
| :---: | :---: |
| Entero | `short`, `unsigned short`, `int`, `unsigned int`, `long`, `unsigned long` |
| Real (punto flotante) | `float`, `double`, `long double` |
| Carácter | `char` |
| Lógico | `bool` |

</center>

### Enteros

Representan números sin parte decimal: positivos, negativos y el cero. Los distintos tipos varían en el espacio que ocupan en memoria y, por lo tanto, en el rango que pueden representar.

``` c
short edad = 20;
int distancia = -300;
long poblacion = 45000000;
unsigned int cantidad = 8;   // solo positivos
```
Los tipos `unsigned` solo admiten valores no negativos, lo que les da el doble de rango positivo.

#### Operadores aritméticos:

<center>

| Operador | Operación | Ejemplo | Resultado |
| :---: | :---: | :---: | :---: |
| `+` | Suma | `2 + 3` | `5` |
| `-` | Resta | `2 - 3` | `-1` |
| `*` | Multiplicación | `2 * 3` | `6` |
| `/` | División entera | `7 / 2` | `3` |
| `%` | Resto de división entera | `7 % 2` | `1` |

</center>

> ❗ La división entre enteros en C es división entera: `7 / 2` da `3`, no `3.5`.

> - `a += b` es lo mismo que `a = a + b` (con todos los operadores aritméticos)
>
> - `a++` es lo mismo que `a = a + 1`

---

### Reales (punto flotante)

Representan números con parte decimal. Se usan cuando la precisión importa como en cálculos científicos, promedios, geometría, etc.

``` c
float temperatura = 36.5;
double precio = 1999.99;
double pi = 3.14159265358979;
```

**Operadores aritméticos:** los mismos que para enteros (`+`, `-`, `*`, `/`), pero la división sí da resultado decimal:

``` c
double resultado = 7.0 / 2.0;  // resultado = 3.5
```

---

### Carácter

Representa un único símbolo, por ejemplo: una letra, un dígito, un signo de puntuación, etc. Se escriben entre comillas simples.

``` c
char letra = 'A';
char digito = '7';
char signo = '?';
```

### Lógico

Solo puede tomar dos valores: `true` (verdadero) o `false` (falso). Es el tipo que devuelven las comparaciones y las operaciones lógicas.

``` c
#include <stdbool.h>

bool aprobado = true;
bool es_mayor = (edad >= 18);
```

#### Operadores relacionales

Reciben dos valores del mismo tipo y devuelven un `bool`:

<center> 

| Operador | Significado | Ejemplo | Resultado |
| :---: | :---: | :---: | :---: |
| `>` | Mayor que | `3 > 3` | `false` |
| `>=` | Mayor o igual | `3 >= 3` | `true` |
| `<` | Menor que | `2 < 5` | `true` |
| `<=` | Menor o igual | `5 <= 3` | `false` |
| `==` | Igual | `5 == 5` | `true` |
| `!=` | Distinto | `5 != 5` | `false` |

</center>

#### Operadores lógicos

Reciben uno o dos `bool` y devuelven un `bool`:

<center> 

| Operador | Nombre | Descripción |
| :---: | :---: | :---: |
| `&&` | AND | `true` solo si ambos son `true` |
| ` \|\|` | OR | `true` si al menos uno es `true` |
| `!` | NOT | Invierte el valor: `true` → `false` |

</center>

## Variables

### ¿Qué son?

Una **variable** es un espacio en memoria al que se le asocia un nombre. Ese nombre la identifica de forma única, es decir, no puede haber dos variables con el mismo nombre en el mismo ámbito. Su contenido puede cambiar a lo largo de la ejecución del programa mediante una asignación.

Una variable tiene tres características fundamentales:

- **Nombre** (identificador): cómo la referenciamos en el código
- **Tipo**: qué clase de valores puede almacenar
- **Valor**: el contenido almacenado en ese momento

La elección de nombre importa. Un buen nombre debe describir qué representa la variable, lo que hace el código mucho más fácil de leer y entender.

No es lo mismo llamar a una variable `x` que llamarla `edad`, el nombre tiene que revelar la intención.

``` c
int x = 21;       // ¿qué es x?
int edad = 21;   // claro y descriptivo
```

---

### ¿Cómo se declaran?

En **Python** no se declaran, simplemente se les asigna un valor.

``` python
edad = 20
promedio = 8.5
letra = 'A'
aprobado = True
```

En **C**, la declaración sigue la forma `tipo nombre;` o `tipo nombre = valor_inicial;`

``` c
int edad;               // declaración sin valor inicial
int edad = 20;          // declaración con inicialización

double promedio = 8.5;
char letra = 'A';
```

---

### Asignación

La asignación es la operación que le da un valor a una variable. En **C** se usa el operador `=`:

``` c
int contador = 0;
contador = contador + 1;  // ahora contador vale 1
```

> 💡 La asignación se evalúa de **derecha a izquierda**. Primero se calcula el lado derecho, y el resultado se guarda en la variable del lado izquierdo.

## Literales

- ¿qué son?

## Constantes

- ¿qué son?
- ¿por qué se usan?
- ¿cómo se declaran?