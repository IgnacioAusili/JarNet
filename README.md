[![stable release](https://img.shields.io/github/release/IgnacioAusili/JarNet.svg?maxAge=3600&label=download)](https://github.com/IgnacioAusili/JarNet/releases)
[![GitHub stars](https://img.shields.io/github/stars/IgnacioAusili/JarNet.svg?style=social)](https://github.com/IgnacioAusili/JarNet/stargazers)
[![GitHub license](https://img.shields.io/github/license/IgnacioAusili/JarNet.svg)](https://github.com/IgnacioAusili/JarNet)


# ![app icon](https://i.imgur.com/cfTCPNG.png) JarNet

Ofrece la capacidad de transferir archivos JAR desde un dispositivo a otro, y poder ejecutarlos remotamente.

En términos más precisos, desde un dispositivo llamemoslo **"dispositivo de origen"**, el programa permite enviar archivos JAR y/o "instrucciones" para su ejecución remota a otro dispositivo llamemoslo **"dispositivo de destino"** desde donde los archivos JAR enviados se almacenarán y se ejecutarán cuando se reciba la orden correspondiente por parte del usuario.

La ejecución de los archivos JAR en el dispositivo de destino implica potencialmente iniciar una aplicación Java contenida en el archivo JAR, lo que permitiría que dicha aplicación se ejecute en el entorno del dispositivo de destino.


### ¿Qué son los archivos "JAR"?

Son archivos que tienen la extension o formato ".jar", en el que se pueden encontrar las aplicaciones escritas en el lenguaje de programacion Java, de una manera compilada.


### ¿Como funciona?

Para funcionar el proyecto se divide en <ins>dos programas</ins>, que deben ser instalados respectivamente en los dispositivos antes mencionados. esos programas son:

- <ins>[JarNetCliente](https://github.com/IgnacioAusili/JarNetCliente)</ins>: Donde se puede realizar el envío de archivos JAR, y la ejecución de los mismos cuando se de la orden por parte del usuario. Este **debe ser instalado en el "dispositivo de origen"**.

- <ins>[JarNetServidor](https://github.com/IgnacioAusili/JarNetCliente)</ins>: Administra la recepción de los archivos JAR. Al recibir un archivo, lo guarda en una ubicación en el disco del "dispositivo de destino". Cuando lo ejecutes, se mantendrá activo hasta que el dispositivo sea apagado o si se finaliza el proceso del programa manualmente. Este **debe ser instalado en el "dispositivo de destino"**.


## Capturas de pantalla

<div style="display:flex">
    <img src="https://github.com/IgnacioAusili/JarNet/assets/50252791/ed877083-fdcf-4541-90e4-8c6137b33b00" alt="Imagen 1" width="434">
    <img src="https://github.com/IgnacioAusili/JarNet/assets/50252791/2450a0a2-ec0d-4c61-b4a6-24cb1d2f27cf" alt="Imagen 2" width="434">
</div>


## Requisitos

Si bien no existen requisitos específicos en términos de recursos del sistema, es necesario cumplir con ciertos requisitos tecnicos para asegurar un funcionamiento correcto del programa, estos son:

- Tanto el servidor como el cliente deben estar conectados a la misma red LAN (No es necesario que esa red tenga internet).
- Los puertos de la red deben estar abiertos. En la mayoría de los casos, los puertos ya estan abiertos por defecto y no requieren intervención adicional. Sin embargo, en caso de que no lo estén, revisa este [apartado](https://www.redeszone.net/tutoriales/configuracion-puertos/abrir-puerto-tcp-udp-router/).
- El programa "Servidor" debe estar activo, cuando se quiera enviar una orden al mismo desde el programa "Cliente".
- Tanto el "dispositivo de destino" y el "dispositivo de origen" deben tener instalado Java, antes de poder ejecutar los programas.

Si estas seguro de cumplir estos aspectos y aún experimentas problemas, quizas pueda ayudarte revisar este [apartado](https://github.com/IgnacioAusili/JarNet#posibles-errores).


## Instrucciones de descarga

Para utilizar correctamente el proyecto, sigue estos pasos:
1. (En caso de no tener Java) Descarga e instala Java, puedes hacerlo desde [aquí](https://www.java.com/en/download/).
2. Descarga la version mas reciende del programa "JarNetServidor", en la maquina que actuara como destino de los archivos JAR, desde este [link](https://github.com/IgnacioAusili/JarNet/releases).
3. Ejecuta el programa "JarNetServidor", una vez ejecutado, se mantendra activo, a la espera de las ordenes del cliente.
4. Descarga la version mas reciente del programa "JarNetCliente", en tu maquina local, desde este [link](https://github.com/IgnacioAusili/JarNet/releases).
5. Ejecuta el programa "JarNetCliente" y verifica que en donde aparece "Conexion:" muestre que esta conectado con el servidor, marcado con un punto verde, de no ser así, revisa este [apartado](https://github.com/IgnacioAusili/JarNet/blob/main/README.md#posibles-errores).


## Posibles errores

Al ser un programa que utiliza conexiones de red, es importante tener en cuenta que pueden ocurrir diversos errores durante su ejecución. Estos errores pueden no ser causados por el programa en sí o por el usuario, sino más bien por la configuración o condiciones de la red en la que se está trabajando. Es fundamental considerar esta posibilidad al analizar y solucionar cualquier problema que pueda surgir durante el uso del programa. A continuación, se detallan los errores más comunes y sus posibles soluciones:

- Puertos ocupados: Puede ocurrir que los puertos necesarios para la comunicación estén siendo utilizados por otros servicios en la red. Para solucionarlo, es recomendable verificar qué proceso o servicio está utilizando esos puertos y liberarlos. También se puede cambiar los números de puerto utilizados por el programa en el código, asegurándose de seleccionar puertos que estén disponibles en la red.

- Desincronización entre programas: En ocasiones, puede producirse una "desincronización" entre el cliente y el servidor, donde uno de ellos espera una respuesta diferente a la que recibe. En caso de que esto suceda, se recomienda cerrar y volver a abrir el cliente. Si el problema persiste, prueba reiniciar el servidor. Para reiniciarlo, se puede utilizar la opción disponible en la interfaz del cliente para reiniciarlo de forma remota, pero hacerlo de esta forma puede no llegar a funcionar. En caso de que esto no funcione, se debe acceder al "dispositivo de destino", buscar el proceso del programa "Servidor" y finalizarlo. Luego, se debe volver a ejecutar el servidor.

- Archivo enviado o a enviar: Puede haber problemas con el archivo específico que se está enviando, como un tamaño excesivo, un nombre demasiado largo o la presencia de caracteres especiales. En este caso, se recomienda probar con un archivo diferente para descartar problemas relacionados con el archivo en sí.

- Por no seguir los requisitos o instrucciones de descarga: Es necesario tener presente que el correcto funcionamiento del programa depende del cumplimiento de ciertos [requisitos](https://github.com/IgnacioAusili/JarNet/blob/main/README.md#requisitos) específicos. Además, se cuenta con una [implementación de descarga](https://github.com/IgnacioAusili/JarNet/blob/main/README.md#instrucciones-de-descarga) que debe ser seguida para garantizar una instalación adecuada.

- Por el antivirus: En circunstancias normales, el programa no debería ser detectado como un virus. No obstante, esto puede variar dependiendo de la configuración de seguridad y del antivirus que esté utilizando. En caso de que esto ocurra, los antivirus suelen ofrecer la opción de agregar exclusiones, lo cual le permitirá añadir el programa a la lista de exclusiones para evitar que sea detectado como un virus.

- Por el sistema operativo: Dado que el programa está desarrollado en Java, se espera que sea compatible con cualquier sistema operativo. Sin embargo, en el caso de sistemas operativos antiguos o poco utilizados, existe la posibilidad de que el programa no funcione correctamente. En tales casos, se recomienda probar el programa en un entorno Windows. Si el programa funciona correctamente en Windows pero presenta dificultades en el sistema operativo habitual, es probable que el problema  se deba a alguna incompatibilidad con dicho sistema operativo.

- Por la version de Java: Existe la posibilidad de que tenga instalada una versión antigua de Java en la cual el programa pueda no funcionar correctamente. En tal caso, se recomienda actualizar Java a la última versión disponible y volver a intentar a ejecutar el programa.

- Por un falso error: A veces, el programa puede mostrar un mensaje de error sobre la conexión, pero en realidad no hay ningún problema real. Esto puede suceder debido a situaciones momentáneas, como demoras en la recepción de datos o conflictos con los puertos utilizados, entre otras situaciones. Si tienes dudas, puedes enviar un archivo y comprobar que todas las funcionalidades continúen operando sin problemas.

Es importante tener en cuenta que estos son solo algunos de los errores posibles y que la solución puede variar dependiendo de la situación específica. Si los problemas persisten, puedes reportarlo por este [medio](https://github.com/IgnacioAusili/JarNet/issues/new).


## Detalles tecnicos

- El proyecto esta dividido en 2 programas, por lo tanto, cada programa tiene su repositorio estos son: [JarNetServidor](https://github.com/IgnacioAusili/JarNetServidor), [JarNetCliente](https://github.com/IgnacioAusili/JarNetCliente).
- Los dos programas del proyecto están desarrollados utilizando el editor de código fuente llamado Visual Studio Code. Por lo tanto, si descargas los programas desde sus respectivos repositorios y los abres utilizando Visual Studio Code, deberían funcionar sin requerir configuraciones adicionales.
- El presente programa ha sido desarrollado exclusivamente por mí y se encuentra bajo licencia de código abierto. Esto significa que tienes la libertad de modificarlo de acuerdo a tus necesidades y preferencias, respetando la licencia.
- Está desarrollado en Java nativo, sin librerías externas.
- Utiliza el protocolo UDP para establecer la conexión entre el servidor y el cliente.
- El codigo fuente de los dos programas, cuenta con una documentación básica en español, proporciona instrucciones sencillas sobre su uso.
- En teoria deberia funcionar para todos los sistemas operativos, siempre y cuando, soporten y tengan instalado Java.
- En teoría, es posible enviar archivos JAR de cualquier tamaño. Sin embargo, en caso de que los archivos JAR sean muy pesados, pueden surgir problemas durante el proceso de transferencia.


## License

~~~
Copyright (C) 2023 Ignacio Inzerilli

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the 
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.

For further information on how to apply and follow the GNU GPL, please
visit <https://www.gnu.org/licenses/>.
~~~


## Disclaimer

Este programa está sujeto a los términos y condiciones establecidos en la Licencia Pública General de GNU (GPL) de software libre. Al utilizar este programa, el usuario reconoce y acepta que:

1. El programa se proporciona "tal cual", sin garantías de ningún tipo, ya sean expresas o implícitas, incluidas, entre otras, las garantías de comerciabilidad, idoneidad para un propósito particular y no infracción. El titular de los derechos de autor y los colaboradores no serán responsables de ningún daño directo, indirecto, incidental, especial, ejemplar o consecuencial que surja del uso o la imposibilidad de uso del programa.

1. El usuario asume la responsabilidad total del uso que haga del programa. El titular de los derechos de autor y los colaboradores no serán responsables de ningún resultado o consecuencia derivada del uso, modificación o distribución del programa. Se recomienda al usuario utilizar el programa de acuerdo con la legalidad vigente y con respeto a los derechos de terceros.

2. El usuario entiende y acepta que cualquier uso indebido o abusivo del programa puede tener consecuencias graves para el afectado y puede incurrir en responsabilidad legal. El titular de los derechos de autor se reserva el derecho de tomar las medidas legales correspondientes en caso de uso malicioso o ilegal del programa.

3. El programa está protegido por derechos de autor y otras leyes de propiedad intelectual. El titular de los derechos de autor retiene todos los derechos sobre el programa y su documentación asociada. Queda expresamente prohibida cualquier reproducción, distribución o modificación no autorizada del programa, salvo en los términos permitidos por la Licencia Pública General de GNU (GPL) de software libre.

Al utilizar este programa, el usuario acepta todos los términos y condiciones establecidos en este disclaimer y en la Licencia Pública General de GNU (GPL) de software libre. Se recomienda leer detenidamente la licencia antes de utilizar el programa.
