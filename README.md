# Cython-Python

Cython ha sido durante mucho tiempo una de las grandes armas secretas del rendimiento de Python, permitiéndote convertir el código Python en C para obtener velocidad. El modo Python puro permite que las herramientas de análisis de código y linting de Python trabajen con los módulos de Cython. La cultura existente de herramientas de Python no tiene por qué terminar en la barrera de Cython.

# Que se logra hacer en el problema de: Planet in orbit

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

![Uploading imagen.png…]()


