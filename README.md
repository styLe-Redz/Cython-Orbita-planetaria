Docente: John Jairo Corredor Franco

Asignatura: Parallel and Distributed Computing

Tema: Rendimiento cython/python: Problema Planeta en Orbita

Estudiante: Christian David Jiménez

# Introducción

El siguiente laboratorio tiene como finalidad presentar una comparativa de rendimiento entre Python y Cython, a través de operaciones aritméticas y ecuaciones diferenciales ordinarias con el fin de realizar una simulación donde se determine la velocidad y movimiento de un cuerpo celeste.

# Cython-Python

Cython ha sido durante mucho tiempo una de las grandes armas secretas del rendimiento de Python, permitiéndote convertir el código Python en C para obtener velocidad. El modo Python puro permite que las herramientas de análisis de código y linting de Python trabajen con los módulos de Cython. La cultura existente de herramientas de Python no tiene por qué terminar en la barrera de Cython.

# Qué se logra hacer en el problema de: Planet in orbit

![imagen](https://user-images.githubusercontent.com/101473794/200685827-7930f19a-07ee-4619-8391-85d2bb929a97.png)

- Se ingresa una posicion y una velocidad inicial en el eje x, y y z
- Se ingresa una masa para el planeta
- Calculo de la fuerza: la gravedad hacia el origen
- Posición del paso de tiempo, según la velocidad
- Velocidad de paso de tiempo, según fuerza y masa

Con estas pruebas se puede estimar el tiempo de ejecucion y la diferencia del mismo cuando se usa Python y Cython.

# Compilar definiciones de tiempo para NumPy

Para crear un código C más eficiente para matrices NumPy, se necesitan declaraciones adicionales. Para empezar, se usa la instrucción cimport de Cython para obtener acceso a los tipos NumPy:

 cimport numpy as cnp
 
La instrucción cimport importa tipos de datos C, funciones y variables C y tipos de extensión. No se puede usar para importar ningún objeto de Python y no implica ninguna importación de Python en tiempo de ejecución.

Al declarar el tipo y las dimensiones de una matriz antes de crearla, Cython puede acceder a la matriz NumPy de manera más eficiente.

# Más mejoras de indexación

Python todavía está realizando una verificación de límites para matrices (es decir, intentar acceder fuera de la memoria asignada da un error) y permite la indexación negativa. Si no se necesita la indexación negativa y se está seguro de que no hay errores fuera de los límites en la indexación, el rendimiento se puede mejorar aún más al deshabilitar la indexación negativa y la verificación de límites para todas las operaciones de indexación dentro de la función. 

# Pruebas de rendimiento

La primera grafica muestra el comportamiento entre dos variables, la carga y el tiempo de ejecucion del programa usando solo Python:

![imagen](https://user-images.githubusercontent.com/101473794/200692581-526f16d8-7e48-486c-a1b7-fcd86ef92231.png)

La segunda grafica muestra el comportamiento entre dos variables, la carga y el tiempo de ejecucion del programa usando Cython:

![imagen](https://user-images.githubusercontent.com/101473794/200692683-33cfb2ff-496f-496f-8adb-fae66ad1bdab.png)

En la tercer grafica se aprecia la relacion entre ambas graficas, notando que el tiempo de ejecucion es mucho menor cuando se usa Cython:

![imagen](https://user-images.githubusercontent.com/101473794/200692866-da839573-4d3c-4cbe-b062-25c1d7e26617.png)

# Análisis y conclusiones

- Cython es un lenguaje que se escribe de forma muy similar a Python, pero permite la utilización de librerías y variables de tipo C. Por tanto, se puede conseguir la velocidad de C manteniendo la simplicidad de sintaxis proporcionada por Python. Además, una de sus grandes versatilidades es que se pueden mezclar definiciones explícitas de variables C con variables de Python, como pueden ser los diccionarios.

- La ventaja esencial de este enfoque, es que al entremezclar perfectamente código Python/C (es decir, C usando <python.h>) es que el código Python existente se puede ajustar a casi la velocidad de C con solo añadir unos pocos tipos estáticos a las declaraciones y haciendo algunas adaptaciones en los bucles críticos -sin necesidad de una interfaz complicada o muy invasiva del código. La velocidad de codificación y la legibilidad del código sigue siendo bastante similar a la que se tiene usando Python. 

- Debido a reducción del consumo general en las estructuras de control (especialmente los bucles), las optimizaciones optimistas y la (limitada) inferencia de tipos, el código Python compilado con Cython normalmente se ejecuta más rápido que en el intérprete CPython 2.6.x, aunque las mejoras absolutas dependen en gran medida del código. 





