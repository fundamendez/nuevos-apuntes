![Fiuba logo](/Uba_fiuba_ingenieria_logo.png){ width=200px }
# Estructuras de control y ciclos

### Estructuras de control

Las estructuras de control permiten modificar el flujo de ejecución de un programa en C, tomando decisiones o repitiendo bloques de código según condiciones lógicas.

#### **If**

Evalua una condicion y determina si es verdadera o no para definir el flujo del programa.

``` c
if (x > 0) {
    printf("x es positivo\n");
}
printf("Fin de ejecución\n");
```
En este fragmento de código se evalúa la condición x > 0 mediante la estructura if. El resultado de dicha evaluación determina si el bloque encerrado entre llaves se ejecuta o se omite. Independientemente de esta decisión, la instrucción printf("Fin de ejecución"); se ejecuta siempre, ya que se encuentra fuera de la estructura condicional.

De esta manera en este ejemplo tenemos dos ejecuciones posibles:

* **Caso 1:** x = 1
``` 
x es positiva
Fin de ejecución 
``` 
En este caso, el valor de x es mayor que cero, por lo que la condición x > 0 resulta verdadera. Como consecuencia, el programa ingresa al bloque del if y ejecuta la instrucción que imprime el mensaje "x es positivo". Finalizada esta ejecución, el flujo del programa continúa de manera secuencial, imprimiendo finalmente el mensaje "Fin de ejecución".

* **Caso 2:** x = 0
``` 
Fin de ejecución 
``` 

En este escenario, el valor de x no cumple la condición x > 0, ya que no es estrictamente mayor que cero. Por lo tanto, el bloque asociado al if no se ejecuta y el programa omite esa instrucción. El flujo continúa directamente con la siguiente línea de código, imprimiendo únicamente el mensaje "Fin de ejecución".

#### **if-else**

Supongamos que ahora queremos que, si la condición del if se cumple, se imprima un mensaje, y en caso contrario se imprima otro distinto. 
Para estos casos se utiliza la estructura **if - else**, que permite definir un bloque de código alternativo que se ejecuta únicamente cuando la condición del if resulta falsa.

Por ejemplo:

``` c
if (x > 0) {
    printf("x es positivo\n");
} else {
    printf("x es negativo o 0\n");
}
```

Ahora tenemos las siguientes salidas posibles:

* **Caso 1:** x = 1
``` 
x es positivo
``` 
En este caso, el valor de x es mayor que cero, por lo que la condición x > 0 resulta verdadera. Como consecuencia, el programa ingresa al bloque del if y ejecuta la instrucción que imprime el mensaje "x es positivo". A diferencia del ejemplo anterior, el bloque else no se ejecuta, ya que este solo se evalúa cuando la condición del if es falsa.

* **Caso 2:** x = 0
``` 
x es negativo o 0
``` 

En este escenario, el valor de x no cumple la condición x > 0, ya que no es estrictamente mayor que cero. Por lo tanto, el bloque asociado al if se omite y el flujo del programa continúa con la ejecución del bloque else, imprimiendo el mensaje "x es negativo o 0".

#### **if-else if-else**

En algunas situaciones es necesario evaluar más de una condición y ejecutar distintos bloques de código según cuál de ellas se cumpla. Para estos casos, C permite encadenar condiciones mediante la estructura **if – else if – else**.
Las condiciones se evalúan en orden, de arriba hacia abajo. El programa ejecuta el primer bloque cuya condición resulte verdadera y luego sale de la estructura condicional. Si ninguna de las condiciones se cumple, se ejecuta el bloque else, si este está presente.

Por ejemplo:
``` c
if (x > 0) {
    printf("x es positivo\n");
} else if (x == 0){
    printf("x es 0\n");
} else {
    printf("x es negativo\n");
}
```

Ahora tenemos las siguientes salidas posibles:

* **Caso 1:** x = 1
``` 
x es positivo
``` 
Si el valor de x es mayor que cero, la primera condición resulta verdadera. En consecuencia, se ejecuta el bloque correspondiente al if, imprimiendo el mensaje "x es positivo". Las condiciones siguientes no se evalúan.

* **Caso 2:** x = 0
``` 
x es 0
``` 

En este caso, la condición x > 0 resulta falsa, por lo que el programa evalúa la siguiente condición. Dado que x == 0 es verdadera, se ejecuta el bloque asociado al else if, imprimiendo el mensaje "x es 0".

*  **Caso 3:** x = -1
``` 
x es negativo
``` 

Si el valor de x es menor que cero, ninguna de las condiciones anteriores se cumple. Como resultado, el programa ejecuta el bloque else, imprimiendo el mensaje "x es negativo".

> <font color="red"> OBS: </font> esta estructura permite cubrir todos los casos posibles para una variable, evitando múltiples estructuras if independientes y asegurando que solo un bloque de código se ejecute en cada ejecución del programa.

##### Diferencias en python

* **if**
``` py
if x > 0:
    print("x es positivo")

print("Fin de ejecución")
```

* **if-else**
``` py
if x > 0:
    print("x es positivo")
else:
    print("x es negativo o 0")
```

* **if-else if-else**
``` py
if x > 0:
    print("x es positivo")
elif x == 0:
    print("x es 0")
else:
    print("x es negativo")
```

> <font color="red"> OBS: </font> si bien C y Python cuentan con estructuras de control conceptualmente similares (condicionales y bucles), existen diferencias importantes en su sintaxis y en la forma en que se escribe y organiza el código.
> 
> En C, los bloques de código se delimitan mediante llaves {} y las condiciones suelen escribirse entre paréntesis. En Python, en cambio, los bloques se definen exclusivamente por la indentación, lo que elimina el uso de llaves pero hace que el correcto espaciado del código sea fundamental para su funcionamiento.

### Ciclos