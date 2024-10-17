# Practica6

## Integrantes
- Uriel Vladimir Alvarez Tapia 20121191
- Miguel Angel Castañeda Garcia 20120015
- Diana Alejandra Mendoza Mendoza 20121226

## Introducción 
Los motores a pasos son dispositivos electromecánicos que convierten impulsos eléctricos en movimientos precisos y discretos. A diferencia de los motores convencionales, los motores a pasos giran en incrementos fijos, lo que permite un control exacto de la posición, velocidad y aceleración. Esto los hace ideales para aplicaciones que requieren un movimiento preciso, como impresoras 3D, CNC, robots y dispositivos automatizados.
El control de un motor a pasos implica gestionar la secuencia y el tiempo de los impulsos eléctricos que determinan su rotación. Debido a la complejidad de este control, los drivers de motores a pasos juegan un papel fundamental. Un driver actúa como un intermediario entre un microcontrolador y el motor, simplificando la generación de señales necesarias para mover el motor en pasos específicos.
El driver recibe las señales de control (como pulsos de paso y dirección) del microcontrolador, ajusta la corriente y voltaje aplicados al motor, y asegura que el motor funcione de manera estable y eficiente. Además, muchos drivers modernos incluyen funciones avanzadas como el control de micro pasos, que permiten dividir los pasos del motor en fracciones más pequeñas para lograr movimientos más suaves y precisos.

## Objetivos
Desarrollar un código de programación (en el microcontrolador de su elección) para el driver de un motor a pasos y que este gire dos veces a la derecha en dos segundos y tres veces a la izquierda en tres segundos. 
## Desarrollo
En primera instancia, se recolectaron todos los materiales necesarios, los cuales se enlistan enseguida
-Fuente de corriente directa 12 V.
-Microcontrolador (Arduino Uno).
-Driver del motor a pasos.
-Motor a pasos. 
Se escogió el Arduino Uno como microcontrolador por su versatilidad al momento de escribir código. 
La conexión de todos los elementos se muestra en la ilustración 1 para la cual se tuvo extremo cuidado debido a que en un primer intentó la conexión presentaba errores y fallos en la ejecución del código. 

![image](https://github.com/user-attachments/assets/f8141824-f688-4f5c-ad34-1eb3f8eecc58)
Ilustración 1: Conexión de los dispositivos.

Seguidamente se procedió a desarrollar la lógica del código de programación.
Primero, dentro de la función “setup” se declararon los pines 3 y 4 del Arduino como salidas digitales. El pin 3 se encargará de los giros del motor mientras que el 4 dictará el momento en que se deba de invertir el giro tal como se indica en la ilustración 2.
De la línea 13 a la 16 se muestra la lógica para dar girar a la derecha dos veces; dado que el driver está configurado para dar una vuelta por 800 pulsos por lo que dentro del ciclo iterativo *for* se puso como límite el doble de dicho valor para que el motor gire dos veces; mandamos un nivel lógico alto por medio de la salida del pin 3 para crear el tren de pulsos para el driver, para lo cual se multiplicó la resolución del driver por 2 (número de giros) y a éste resultado (en Hz) se sacó el inverso para obtener su equivalente en segundos dando como resultado 625 µs; dicho valor se pasó como parámetro a la función delayMicrosecond() para obtener el tren de pulsos mencionado. 
Después de girar a la derecha; el motor espera un segundo e invierte el sentido del giro con la sentencia de la línea 19.
Se implementa la misma lógica para las vueltas a la izquierda; la única diferencia es que en este sentido deberá de girar 3 veces por lo que los pulsos del driver se deberán de multiplicar por 3 tal como se observa en la línea 20 y hacer el cálculo de manera similar para el periodo del tren de pulsos que, en este caso resulta en 1250 µs. Finalmente generamos nuevamente el tren de pulsos para que el driver lo interprete y haga girar el motor. 

![image](https://github.com/user-attachments/assets/422e2615-7bad-4bac-aca0-6b53e798352d)
Ilustración 2: Código en Arduino para el driver del motor a pasos.

## Resultados
Los resultados obtenidos fueron guardados en archivos de video, por lo que es imposible mostrarlo en este documento; sin embargo, la ilustración 3 muestra una captura de pantalla de dicho video donde se captura el momento en el que el motor a pasos estaba girando a la derecha dando por catalogada como cumplido el objetivo de la practica anteriormente descrito.
![image](https://github.com/user-attachments/assets/38b7633a-5053-47eb-bb53-75213ea52bb0)
Ilustración 3: Captura de pantalla del momento en que el motor gira a la derecha.


## Conclusiones
- **Uriel Vladimir Alvarez Tapia:** El control de motores a pasos es una parte fundamental e indispensable en el ambito de la robotica, gracias a esta practica fue posible realizar el control de un motor a pasos mediante un driver de un grado mas industrializado. Esto selogro mediante un microcontrolador que al enviar la cantidad de pulsos y a la frecuencia adecuada controla el sentido y la velocidad de giro, permitiendo mantener una alta exactitud en la posicion del equipo, así como el tiempo que le toma ejecutar el movimiento.
- **Miguel Angel Castañeda Garcia:** En conclusión, el uso de motores a pasos controlados mediante un driver permite un control preciso y confiable de movimientos en una amplia gama de aplicaciones. En el caso específico, el motor a pasos realizó dos giros completos a la derecha en un lapso de dos segundos, y posteriormente ejecutó tres giros completos a la izquierda en tres segundos, mostrando la capacidad de control preciso de la velocidad y dirección.
El control fue llevado a cabo utilizando un Arduino Uno como microcontrolador, el cual envió las señales necesarias al driver del motor. Esta combinación hace posible la integración de estos sistemas en proyectos de robótica, automatización y control numérico, abriendo la puerta a una variedad de innovaciones tecnológicas.

- **Diana Alejandra Mendoza Mendoza:**  En esta práctica, se utilizó un ciclo for para apilar fusibles ajustando el eje Z según la medida de cada uno. A pesar de un pequeño error de medición que afectó la posición de liberación del fusible, el proceso fue exitoso y se logró observar cómo los ciclos for permiten realizar tareas repetitivas con modificaciones precisas en cada iteración. Esto demostró la importancia de los ciclos en la programación de robots industriales, brindando eficiencia en tareas automatizadas.**
