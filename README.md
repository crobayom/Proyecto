# Astucia Naval
#### Cristian Eduardo Robayo Martinez
#### Carlos David Pinto Guzman


## Definicion de la Alternativa: 

La alternativa que elegimos es de caracter libre y propositiva, mantenemos el orden anterior continuando con juegos; En este caso, el conocido juego de estrategia, nuestra idea es replicarlo (dentro de lo posible) lo mas identico al original, es decir, 4 tableros (2 para las posiciones de los barcos y 2 para los intentos de hundirlos), con la posibilidad de el propio jugador ubicar sus barcos cual si fuera en el juego fisico (en cualquier lugar siempre y cuando este orientado vertical y horizontalmente y este dentro de los limites del tablero) 

### Juego

AStucia Naval

![image](https://github.com/user-attachments/assets/4cf83fd4-be92-4a83-b82e-be448ffbe7a4)

Justicia Naval es un juego de mesa de estrategia y habilidad donde los jugadores asumen el rol de comandantes de barcos de guerra en una serie de batallas en el mar. El objetivo principal es hundir los barcos del oponente utilizando tácticas, conocimiento del terreno y toma de decisiones rápidas.

El juego suele estar basado en una cuadrícula o tablero donde los jugadores colocan sus barcos de manera estratégica, tratando de ocultarlos de su oponente mientras intentan localizar y destruir los barcos enemigos. La mecánica más común involucra lanzar "ataques" en puntos específicos del tablero, con el fin de dar en el blanco de los barcos rivales, lo cual se va indicando con marcas de acierto o fallo.

Elementos necesarios de Justicia Naval:

Tablero dividido en coordenadas, con filas y columnas.
Barcos de diferentes tamaños (generalmente un destructor, una fragata, un portaaviones, etc.) que deben ser ubicados de forma oculta al contrario.
Los jugadores turnan para "atacar" en ubicaciones específicas del tablero rival, y si aciertan, el oponente tiene que revelar un impacto en ese punto.
El juego finaliza cuando uno de los jugadores hunde todos los barcos enemigos.
Este tipo de juegos pone a prueba la lógica y la capacidad de anticiparse a los movimientos del oponente, ofreciendo tanto estrategia como tensión a medida que los barcos de ambos jugadores se van destruyendo. En muchos casos, el título "Justicia Naval" puede ser una variante o un nombre específico de un juego que sigue estas mismas mecánicas.

## Algoritmos utilizados


## 1. Inicialización de tableros (Algoritmo de construcción de matrices):

- Se usa un bucle anidado (for) para crear e inicializar matrices (tableroA, tableroB, etc.), que representan los tableros del juego.
- Cada tablero es una matriz de tamaño maximo x maximo inicializada con ceros.

   
```python
maximo = 4

# Crear una matriz de 4x4 llena de ceros
tablero = [[0] * maximo for _ in range(maximo)]

# Mostrar la matriz
for fila in tablero:
    print(fila)

# Modificar una celda específica
tablero[2][3] = 1

print("\nMatriz después de modificar una celda:")
for fila in tablero:
    print(fila)
```


## 2. Validación de entrada del usuario (Algoritmo de control de flujo):

- Se emplean bucles while para asegurar que las coordenadas ingresadas sean válidas (dentro de los límites del tablero y siguiendo las reglas de orientación de los barcos).
- Se utilizan condicionales (if) para manejar errores y restricciones de entrada.

```python
numero = -1

while numero < 1 or numero > 5:
    numero = int(input("Ingresa un número entre 1 y 5: "))
    if numero < 1 or numero > 5:
        print("Número fuera de rango. Inténtalo de nuevo.")

print(f"Has ingresado un número válido: {numero}")
```


## 3. Colocación de barcos (Algoritmo de asignación de valores en una matriz):

- Dependiendo de la orientación elegida por el usuario (vertical u horizontal), se coloca un submarino de dos casillas en el tablero.
- Se verifican las restricciones de distancia mediante fabs() o abs() para asegurar que los barcos se coloquen correctamente.

```python
tablero = [[0] * 4 for _ in range(4)]

orientacion = int(input("Elige la orientación (1: vertical, 2: horizontal): "))

fila = int(input("Elige la fila inicial (1-4): ")) - 1
columna = int(input("Elige la columna inicial (1-4): ")) - 1

tablero[fila][columna] = 1  # Colocar primera parte del barco

if orientacion == 1 and fila < 3:  # Vertical
    tablero[fila + 1][columna] = 1
elif orientacion == 2 and columna < 3:  # Horizontal
    tablero[fila][columna + 1] = 1

for fila in tablero:
    print(fila)
```


## 4. Simulación de turnos (Algoritmo de control de flujo en bucle while):

- Se usa un bucle while que se ejecuta hasta que uno de los jugadores pierda todos sus barcos.
- Cada jugador tiene un turno alternado para atacar, en el cual:
- Introduce coordenadas para disparar.
- Se actualiza el tablero de ataques y el tablero del oponente.
- Se verifica si un disparo acertó (if tableroB[...] == 1).
- Se imprime el estado de los tableros.

```python
turno = 1  # Empieza el jugador 1

while turno <= 5:  # Simulamos 5 turnos
    print(f"Turno del jugador {turno % 2 + 1}")
    
    # Aquí iría la lógica del juego, como ingresar coordenadas de ataque

    turno += 1  # Cambiar de turno

print("Fin del juego")
```


## 5. Detección de victoria (Algoritmo de búsqueda en una matriz):

- Se usa un bucle for que recorre cada fila del tablero verificando si quedan barcos (1 en la matriz).
- Si ya no quedan barcos (1), el jugador pierde.
- Se imprime el resultado según la condición (if existencia1 == False o if existencia2 == False).

```python
tablero = [
    [0, 0, 1, 0],
    [0, 0, 0, 0],
    [1, 0, 0, 0],
    [0, 0, 0, 0]
]

quedan_barcos = any(1 in fila for fila in tablero)

if quedan_barcos:
    print("Aún quedan barcos en el tablero.")
else:
    print("¡No quedan barcos! Fin del juego.")
```


## 6. Temporizadores y limpieza de pantalla (Algoritmo de espera y actualización visual):

- sleep(1) se usa para generar pausas entre acciones, simulando un efecto de cuenta regresiva.
- system("cls") intenta limpiar la pantalla.

```python
import time
import os

for i in range(5, 0, -1):
    print(f"{i}...")
    time.sleep(1)
    os.system("cls" if os.name == "nt" else "clear")  # Borra la pantalla

print("¡Comienza el juego!")
```


### Diagrama de flujo:
#### Enlace del diagrama de flujo en mermaid:

https://mermaid.live/edit#pako:eNqNk91umzAUgF_F8lUq0ahgaAiVOq2haZM26U-qXQx6cQou8QZ2ZkBag_JIu9oDTFpfbI75EdOmdVxxfL5zjv3JrnAkYoo9nEjYrNGDfxJypL73g8GMs4iJgwN0eHiKzgIdQsq2IFEBTymVIn-s4TONTIJ5mUAsJDJRJFIRAXoCGXXURFN-R1l_pXxNnQcTkTHKt4CeIacopggK-FLShjrX1DR4KCUXKpuibnZDTDVx0dsTTVlCUZ3diFyd5vU7_6Pzha67rH7-QLNsA1Eh0LtdnbpUKbR6_aaJWbBQ21YuWENR3mp57OFLoel5S9ez1KHSlMUtOdPMVfCBSvbM9ljOkMJi4L_LmddgHVz1t3PdqOjkNhXXOrvoSf8_DQtdt6waB62CZX_mzZsKlj0Ft_9UcKOZu7cV3NZgHdz1tzPtrTUz7wOfFlRmjKuGCfC9gqbPvQZWg8GUcX2BPpU0Ubc95NjAmaoBFqtnUe3pEBdrmtEQe-o3Bvk5xCHfKQ7KQqxeeIS9QpbUwFKUyRp76mi5ispNDAX1Gai3lXWrG-AfhcjaEhVir8JfsWeNhiPTHRPXGhHbJSYhBn7BnjkemsR0TYscjcaWYzs7A291A3t47DjEcQlxx0c2ObYNTGNWCLmon7R-2btfrn4vEA


## Solucion Preliminar

En el archivo adjuntado

## Problemas 

[] Entrada de los barcos en las posiciones que el usuario elija

[] Distincion entre jugadores

[] No sobreposicionamiento de barcos (uno sobre otro)


## Conclusion

El proyecto fue una gran herramiento para usar las herramientas aprendidas como funciones, condicionales y demas.
Sin embargo lo mas importante dentro del proyecto fue el uso de la logica de programacion, para racionalizar y verificar cualquier proceso que se tratara de llevar a cabo.
Fue la herramienta principal la hora de tomar decisiones de diseño.

