# RP2 P3 Constrained Application Protocol

## Alumnos

Sergio Semedi Barranco

Lucas Segarra Fernández

## Guión

__Ejecuta los programas servidor y cliente CoAP del directorio__
__examples.__
__Estudia sus opciones y parámetros de configuración. ¿En qué puertos y bajo qué protocolos__
__escucha el servidor CoAP tras su arranque?__

	$ netstat -ln

tcp6       0      0 [::]:5683               [::]:*                  LISTEN     
tcp6       0      0 [::]:5684               [::]:*                  LISTEN
udp6       0      0 [::]:5683               [::]:*                             
udp6       0      0 [::]:5684               [::]:*

Investiga las opciones disponibles en el cliente y servidor con respecto a la cantidad
de mensajes de depuración a mostrar. Ejecuta el servidor CoAP con suficiente nivel
de detalle en los mensajes de depuración


Para ello puedes ejecutar tanto el cliente o el servidor con la opción -v 10

./co-server -v 10
Dec 18 19:25:05 DEBG created UDP endpoint [::]:5683
Dec 18 19:25:05 DEBG created DTLS  endpoint [::]:5684
Dec 18 19:25:05 DEBG created TCP endpoint [::]:5683
Dec 18 19:25:05 DEBG created TLS endpoint [::]:5684
Dec 18 19:25:17 DEBG   [::1]:5683 <-> [::1]:46689 (if1) UDP: new incoming session
Dec 18 19:25:17 DEBG   [::1]:5683 <-> [::1]:46689 (if1) UDP: received 15 bytes
:1 t:CON c:PUT i:736a {} [ Uri-Path:time ] :: '1000\x0A'
Dec 18 19:25:17 DEBG call custom handler for resource 0x2f0df10e
Dec 18 19:25:17 DEBG   [::1]:5683 <-> [::1]:46689 (if1) UDP: sent 4 bytes
Dec 18 19:27:15 DEBG  [::1]:5683 <-> [::1]:46689 (if1) UDP: session closed


¿Qué recursos están disponibles en el servidor? Estudia el código fuente del mismo
para observar la correlación entre los recursos descubiertos y los programados en el
código. Averigua el significado de los atributos rt, ct, if y title

Para iniciar los recurso expuestos, el servidor expone recursos con este metodo:

init_resources(coap_context_t ctx)

Hay una macro definida con char * para devolverla en la / inicial del servidor

#define INDEX "This is a test server made with libcoap (see https://libcoap.net)\n" \
                "Copyright (C) 2010--2016 Olaf Bergmann <bergmann@tzi.org>\n\n"


Una forma de descubrir una ruta sería la siguiente:

    r = coap_resource_init((unsigned char \*)"ttime", 5, COAP_RESOURCE_FLAGS_NOTIFY_CON);











