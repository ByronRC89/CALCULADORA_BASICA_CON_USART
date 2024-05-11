# CALCULADORA_BASICA_CON_USART
Este código es un programa para un microcontrolador STM32L0 que implementa una calculadora básica con una interfaz de usuario basada en teclas y una visualización en display de siete segmentos. 

Se configuran los pines del microcontrolador para la comunicación USART2 y la interfaz de teclado y display de siete segmentos.
Bucle principal (main): Este bucle infinito llama a tres funciones principales en cada iteración:
   -``` keyboard_config():``` Configura los pines del teclado.
   -``` key_pressed():``` Detecta qué tecla se ha presionado en el teclado y realiza las operaciones correspondientes.
   -``` calculador():``` Realiza las operaciones aritméticas dependiendo del estado actual del programa y muestra el resultado en los displays de siete segmentos.

en el codigo tenemos primero las librerias como lo vemos en esta imagen.
 ![image](https://github.com/ByronRC89/CALCULADORA_BASICA_CON_USART/assets/159856194/4fccc63b-427f-48fb-aa17-a4571c1549ff)
 

las cuales son las responsables para llamar ciertas funciones necesarias para usart2, gpio,RCC y otras configuraciones.
luego tenemos la llamada de funciones``` usart2(write,putstring,putstring_E y Read)```
luego tenemos las variables de estado para los digitos 0 que es el de entrada, digito 1 es el primer valor guardado y digito 2 es el segundo valor guardado
![image](https://github.com/ByronRC89/CALCULADORA_BASICA_CON_USART/assets/159856194/df0020b5-7cb6-46f2-b825-152f62e1c246)


defininimos los puertos de la siguiente forma.
GPIOB---- definimos 7 puertos libres para el dispaly 7 segmentos
GPIOA---- definimos PA0 y 1 como activaciones para el comun de los display.
GPIOC---- definimos PC5, PC6, PC8 Y PC9 como entradas pull-up
GPIOB , GPIOC, GPIOA, ---- PB11, PC7, PC4,PA9 como salidas en modo high para la lectura de presencia en 1 en todas las filas y columnas.

![image](https://github.com/ByronRC89/CALCULADORA_BASICA_CON_USART/assets/159856194/81a9fe53-1f80-454d-a489-26de156005ae)

el escaneo comienza con detectar cero voltios en las columnas, dependiendo de que tecla se haya presionado en un keypad de 4x4,

descripcion de las teclas.
las teclas numericas quedan en el codigo definidas para encender cada segmento segun su numeracion, la tecla A define la operacion suma, la tecla B define la operacion resta, la tecla C es multiplicacion, la letra D es la division.
la tecla ´#´ es programada para poder borrar los datos de operacion y los digitos guardados 
la tecla ¨*¨ es programada como un enter, que le da la instruccion de guardar el primer valor.
descripcion de la tecla #
![image](https://github.com/ByronRC89/CALCULADORA_BASICA_CON_USART/assets/159856194/49710607-baae-4b0d-a273-45d49e5cd8ae)

descripcion de la tecla *
![image](https://github.com/ByronRC89/CALCULADORA_BASICA_CON_USART/assets/159856194/73e446d9-4717-4b86-ba85-9174a445190d)

**descripcion general para operar** 
para operar es necesario seguir los siguientes pasos, ingresar primer digito, luego se presiona  la tecla * para poder guardar el primer valor que pasa a ser digito 2, luego se presiona el segundo digito que es guardado en digito 1, luego se presiona la operacion deseada en las teclas A, B, C, D y desplegara el resultado en los display de 7 segmentos y en la consola de comunicacion serial de 9600 baud a 16Mhz, en este caso usamos la consola arduino.
descripcion de las operaciones en la letra A
![image](https://github.com/ByronRC89/CALCULADORA_BASICA_CON_USART/assets/159856194/33c3257e-7263-4091-8997-88305f8a637c)

descripcion de las operaciones en la letra B
![image](https://github.com/ByronRC89/CALCULADORA_BASICA_CON_USART/assets/159856194/65763dab-442e-458f-989b-db75f04ea4d2)

descripcion de las operaciones en la letra C
![image](https://github.com/ByronRC89/CALCULADORA_BASICA_CON_USART/assets/159856194/1dff5290-11cd-421f-b03c-d43916f83782)

descripcion de las operaciones en la letra D
![image](https://github.com/ByronRC89/CALCULADORA_BASICA_CON_USART/assets/159856194/65e61a7f-2415-43cf-bb53-4a2117407078)


```USART2_putstring_E("operacion suma"){}```; con esta operacion imprimimos el titulo de la operacion realizada.
```USART2_write("escrito");``` aqui imprimimos en la consola el valor ASCII guardado en la variable ¨escrito¨
![image](https://github.com/ByronRC89/CALCULADORA_BASICA_CON_USART/assets/159856194/8733348e-5e14-4f20-b333-607e6ba6747d)

A continuacion dejaremos un breve video que explica la funcionadidad del codigo con la placa de desarrollo stm32 y la consola serial.
ingresa al siguiente link.
video: https://youtu.be/T8z1FTxUo4M
![image](https://github.com/ByronRC89/CALCULADORA_BASICA_CON_USART/assets/159856194/ff321233-05cf-4861-a1b5-7f421eeebfd1)


