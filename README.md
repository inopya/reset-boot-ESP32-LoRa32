# reset boot en placas ESP32 LoRa32
Solucion a error de no poder cargar codigo en placas ESP32-LoRa32 desde Arduino IDE.

El error puede ser algo similar a: 
"A fatal error occurred: Failed to connect to ESP32: Timed out waiting for packet header" 
o alguna variante, pero el resultado es el mismo tras un buen rato de ver puntos suspensivos en nuestro monitor serie del IDE, el proceso de carga no puede completarse y nuestrsa placa permanece "muerta"

No entremos en pánico... Nuestro ESP32 ha tenido un error durante la ultima carga de un sketch y se ha dañado el bootloader que lo hace reconocible para el IDE de Arduino

# Primera opcion 
(NO es necesario ningun material extra)

1) Conecta la placa por USB como haces normalmente para grabar un nuevo programa.
2) Pulsa el boton de RESET de la placa ESP32/LoRa32 (y dejalo pulsado).
3) Haz una subida normal un sketch cualquiera a la placa (manteniendo pulsado el boton de RESET)
4) Estate atento a las cosas que van saliendo por el monitor serie del IDE...  y cuando veas que dice que empieza el proceso de carga, suelta el boton de reset
es decir cuando empieza a mostrar los puntitos suspensivos y el porcentaje de carga.

Con algo de suerte esto te sacará del apuro. Aunque de entrada te digo que en la mayoría de los casos no funciona y hemos de pasar al plan B

# Segunda opcion
(Plan B, necesitaras una protoboard, una resistencia de 1k y un par de cables dupont)

1) Pon una resistencia de 1k en la protoboad \*
2) Conecta un cable desde pin IO0 de tu ESP/Lora hasta un extremo de la resistencia.
3) Conecta otro cable desde un pin GND de la placa hasta el otro extremo de la resistencia.
4) Inicia el proceso de carga de un sketch cualquiera, por ejemplo un humilde "blink"

\*Podriamos hecer el puente directemente entre IO0 y GND, pero no sabemos a priori si ese pin por algun motivo ha quedado configurado como salida en cuyo caso estariamos provocando un cortocircuito. Es cierto que tambien podriamos medir con el multimetro la salida IO0, pero tambien podia existir en ella un PWM que "nos despieste".
Así que nos curaremos en salud haciendo ese puente resistivo. 


![](./reset-bootloader-lora-esp-32.png)
