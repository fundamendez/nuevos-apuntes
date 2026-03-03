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

<center>

| Tipos genéricos | Tipos de dato en C |
| :---: | :---: |
| Entero | `short`, `unsigned short`, `int`, `unsigned int`, `long`, `unsigned long` |
| Real (punto flotante) | `float`, `double`, `long double` |
| Carácter | `char` |
| Lógico | `bool` |

</center>

### Enteros

Representan números sin parte decimal: positivos, negativos y el cero.

En C existen distintas variantes del tipo entero. La diferencia entre ellas es cuántos bytes ocupan en memoria: a más bytes, más valores distintos se pueden representar y mayor es el rango.

``` c
short edad = 20;
int distancia = -300;
long poblacion = 45000000;
unsigned int cantidad = 8;   // solo positivos
```
Los tipos `unsigned` son variantes que solo admiten valores no negativos. Al no necesitar representar negativos, pueden llegar al doble de valor máximo positivo con los mismos bytes.

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
int edad = 21;   // más claro y descriptivo
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

### ¿Qué son?

Un **literal** es un valor escrito tal cual en el código fuente. Es el valor en sí mismo, no una variable ni una constante.

``` c
if (edad >= 18) { // 18 es un literal
	printf("Soy mayor de edad");
}
```

## Constantes

### ¿Qué son?

Una **constante** es un espacio en memoria, similar a una variable, pero cuyo valor se establece una sola vez y **no puede cambiar** durante la ejecución del programa.

---

### ¿Por qué se usan?

- **Claridad**: hacen el código más legible.
- **Mantenimiento**: si el valor necesita cambiar, solo se modifica en un solo lugar.
- **Seguridad**: el compilador no permite que se modifique el valor en cualquier parte del código.

---

### ¿Cómo se declaran?

En **C**, se usa la palabra clave `const` antes del tipo:

``` c
const double PI = 3.1415;
const int MAX_INTENTOS = 3;
const char SEPARADOR = '-';
```

Intentar modificar una constante produce un error de compilación:

``` c
const double PI = 3.1415;
PI = 3.0;  // Esto NO está permitido, no compilará
```

---

### Constantes vs Literales

Usar literales dispersos a lo largo del código hace que sea más difícil de leer y mantener. Como aparecen sin nombre ni contexto, el lector tiene que adivinar qué representan. Además, si ese valor necesita cambiar, hay que encontrar y modificar cada aparición manualmente, lo que es fácil de olvidar y puede introducir errores.

Por ejemplo, si las edades o el IVA cambian, este código obliga a buscar cada 18, 60 y 1.21 en todo el programa:
``` c
if (edad >= 18 && edad <= 60) {
    precio = precio * 1.21;
}
```

Con constantes, el valor se define en un solo lugar y cualquier cambio se propaga automáticamente a todo el código que las usa:
``` c
const int EDAD_MINIMA = 18;
const int EDAD_MAXIMA = 60;
const double IVA = 1.21;

if (edad >= EDAD_MINIMA && edad <= EDAD_MAXIMA) {
    precio = precio * IVA;
}
```

>❗ Siempre que un literal represente algo con significado, se debe reemplazar por una constante con un nombre descriptivo.