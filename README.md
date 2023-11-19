# QM2515-Tarea-Nro-4
Programas de la materia de Introducción a la Quimiometría. Tarea Nro. 4
# Problema #1: Método gráfico para determinar el coeficiente de resistencia.

Este código calcula y grafica la relación entre la velocidad de un paracaidista y el coeficiente de resistencia aerodinámica, combinando cálculos numéricos y visualización gráfica. Utiliza numpy para operaciones matemáticas, scipy.optimize para resolver ecuaciones y matplotlib.pyplot para crear gráficos.

Comenzamos definiendo parámetros clave: la masa del paracaidista (m), la gravedad (g), la velocidad deseada (v) y el tiempo de caída (t). Estos parámetros se utilizan en la función `calcular_coeficiente_resistencia`, que calcula el coeficiente de resistencia (c) necesario para alcanzar la velocidad deseada en el tiempo dado. Dentro de esta función, se define `ecuacion`, que representa la relación matemática entre c y la velocidad a lo largo del tiempo, y se utiliza `fsolve` de scipy.optimize para encontrar el valor de c que satisface esta ecuación.

Luego, el código genera un rango de posibles valores de c y calcula la velocidad correspondiente para cada uno. Estos cálculos se visualizan en un gráfico creado con matplotlib.pyplot, donde se traza la relación entre el coeficiente de resistencia y la velocidad. Se incluyen líneas para destacar la velocidad deseada y el coeficiente de resistencia calculado.

# Problema #2: Regla de Cramer.

Este código en Python resuelve un sistema de ecuaciones lineales utilizando la biblioteca NumPy. En primer lugar, se importa NumPy como 'np'. Luego, se definen los coeficientes de la matriz de coeficientes 'A' y los términos independientes 'B' del sistema de ecuaciones.

A continuación, se calcula el determinante de la matriz 'A' utilizando la función 'np.linalg.det()'. Si el determinante es igual a cero, se imprime un mensaje indicando que el sistema no tiene una única solución.

Si el determinante no es cero, se procede a calcular los determinantes para cada variable 'x1', 'x2' y 'x3' mediante la creación de matrices que reemplazan las columnas correspondientes de 'A' con el vector 'B'. Luego, se calculan las soluciones 'x1', 'x2' y 'x3' dividiendo estos determinantes por el determinante de 'A'.

# Problema #3: Regla del Trapecio.

Este código utiliza la regla del trapecio para calcular una aproximación de la integral de una función, basándose en datos tabulados. El proceso comienza con dos listas de datos: `x_valores`, que son los puntos en el eje x, y `Fx_valores`, que representan los valores de la función en esos puntos.

La regla del trapecio es un método de integración numérica que estima el área bajo una curva dividiéndola en trapecios, en lugar de rectángulos como en el método del rectángulo. Para aplicar esta regla, primero se establece `h`, la distancia entre los puntos consecutivos en el eje x, que en este caso es uniforme y vale 0.1. Luego, se calcula la suma de los valores de la función (Fx_valores) en los extremos (el primero y el último valor) y el doble de la suma de los valores intermedios. Esta suma representa la suma de las áreas de los trapecios.

Finalmente, se aplica la fórmula de la regla del trapecio: la integral aproximada es igual a `h/2` multiplicado por la suma calculada anteriormente. El resultado se almacena en `aproximación_de_la_integral` y se muestra con un mensaje que indica que es una integral aproximada obtenida mediante este método.


# Programa #4: Reglas de Simpson.

En este código, calculamos la integral aproximada de una función utilizando la Regla de Simpson 1/3, un método numérico para la integración. Comenzamos definiendo dos listas: `x_valores` y `f_x_valores`. La lista `x_valores` contiene los puntos en el eje x donde la función es evaluada, y `f_x_valores` contiene los valores de la función en esos puntos. Luego, calculamos el valor de `Delta x`, que es la distancia entre cada par de puntos consecutivos en el eje x, asumiendo que todos los intervalos tienen el mismo tamaño.

Después, definimos una lista llamada `mult` que contiene los multiplicadores para cada punto según la Regla de Simpson 1/3. Esta regla alterna entre multiplicar los valores de la función por 4 y por 2, excepto en los extremos, que siempre se multiplican por 1. Posteriormente, creamos una función llamada `reglas_de_simpson` que toma `Delta x`, los valores de `x`, y los multiplicadores como argumentos. Dentro de esta función, aplicamos la Regla de Simpson 1/3. Multiplicamos cada valor de la función por su multiplicador correspondiente y sumamos todos estos productos. Luego, multiplicamos esta suma por `Delta x` dividido entre 3 para obtener la integral aproximada.

Finalmente, redondeamos el valor de la integral a un decimal para facilitar su lectura.

# Programa #5: Resolución de Ecuaciones Diferenciales de Primer Orden.

# Método Analítico.

En este programa, utilizamos el método analítico para resolver ecuaciones diferenciales de primer orden. Importamos librerías como `sympy` para trabajar con matemáticas simbólicas y `matplotlib.pyplot` junto con `numpy` para las gráficas y cálculos numéricos. Definimos `t` y `y` como símbolos y funciones respectivamente, para representar variables y funciones en las ecuaciones diferenciales.

El usuario introduce una ecuación diferencial y condiciones iniciales, las cuales son procesadas y convertidas a expresiones de `sympy`. Utilizamos `dsolve` para resolver la ecuación diferencial de manera simbólica, y con `lambdify` convertimos la solución a una función numérica que luego utilizamos para calcular valores y graficar la solución.

# Método de Euler.

El método de Euler es un procedimiento numérico básico para resolver ecuaciones diferenciales ordinarias (EDO). Partimos de una condición inicial y utilizamos una fórmula simple para avanzar paso a paso a lo largo de la función. En el código, transformamos la ecuación diferencial dada por el usuario para que se ajuste al formato requerido por Euler. La función `ecu_euler` es crucial aquí: utiliza `lambdify` para convertir la expresión simbólica en una función numérica, que es esencial para evaluar la ecuación en puntos específicos.

La función principal del método de Euler es `aplicar_euler`. Aquí, creamos un arreglo de valores de tiempo `t` desde el inicio hasta el final del intervalo deseado, con pasos definidos por `h` (tamaño del paso). Inicializamos un arreglo `y` para almacenar las soluciones. Comenzamos con la condición inicial y luego, iterativamente, aplicamos la fórmula de Euler: `y[i] = y[i-1] + h * ecu_euler(y[i-1], t[i-1])`. Esto significa que el siguiente valor se calcula a partir del valor anterior más el producto del tamaño del paso y la derivada (calculada por `ecu_euler`) en el punto anterior.

# Método de Runge-Kutta.

El método de Runge-Kutta (específicamente RK4, que es la cuarta versión y la más utilizada) es una técnica más avanzada y precisa para resolver EDOs. Este método calcula varias pendientes (derivadas) en cada paso y toma un promedio ponderado de estas para determinar el siguiente valor.

En nuestro código, la función `RK` implementa este método. Iniciamos con los mismos pasos y valores iniciales que en Euler. La diferencia principal radica en cómo calculamos el nuevo valor de `y`. Para cada paso, calculamos cuatro pendientes:

- `k1` es la pendiente al inicio del intervalo.
- `k2` es la pendiente en el punto medio del intervalo, usando `k1` para estimar el valor de `y` a la mitad del intervalo.
- `k3` es otra estimación de la pendiente en el punto medio, pero usando `k2` para la estimación de `y`.
- `k4` es la pendiente al final del intervalo, usando `k3` para estimar `y` al final.

Luego, el nuevo valor de `y` se calcula como un promedio ponderado de estas cuatro pendientes: `y[i] = y[i-1] + (h / 6) * (k1 + 2 * k2 + 2 * k3 + k4)`. Este promedio ponderado proporciona una aproximación más precisa de la función en el siguiente punto.
