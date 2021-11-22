# Laboratorio 9 - Ana Gabriela Silva Briceño

### Parte 1 - Escalabilidad vertical

1 - 3. Instalaciones

![](https://github.com/gabrielaasilva/SilvaAnaGabriela_Lab08ARSW-/blob/master/Imágenes/1.png)

4. Para instalar la aplicación adjunta al Laboratorio, suba la carpeta `FibonacciApp` a un repositorio al cual tenga acceso y ejecute estos comandos dentro de la VM:

![](https://github.com/gabrielaasilva/SilvaAnaGabriela_Lab08ARSW-/blob/master/Imágenes/2.png)

5. Para ejecutar la aplicación puede usar el comando `npm FibinacciApp.js`, sin embargo una vez pierda la conexión ssh la aplicación dejará de funcionar. Para evitar ese compartamiento usaremos *forever*. Ejecute los siguientes comando dentro de la VM.

    `npm install forever -g`

    `forever start FibinacciApp.js`

6. Antes de verificar si el endpoint funciona, en Azure vaya a la sección de *Networking* y cree una *Inbound port rule* tal como se muestra en la imágen. Para verificar que la aplicación funciona, use un browser y user el endpoint `http://xxx.xxx.xxx.xxx:3000/fibonacci/6`. La respuesta debe ser `The answer is 8`.

![](https://github.com/gabrielaasilva/SilvaAnaGabriela_Lab08ARSW-/blob/master/Imágenes/3.png)

7. La función que calcula en enésimo número de la secuencia de Fibonacci está muy mal construido y consume bastante CPU para obtener la respuesta. Usando la consola del Browser documente los tiempos de respuesta para dicho endpoint usando los siguintes valores:
    * 1000000
    ![](https://github.com/gabrielaasilva/SilvaAnaGabriela_Lab08ARSW-/blob/master/Imágenes/7-1000000.png)
    
    * 1040000
    ![](https://github.com/gabrielaasilva/SilvaAnaGabriela_Lab08ARSW-/blob/master/Imágenes/7-1040000.png)

    * 1090000  
    ![](https://github.com/gabrielaasilva/SilvaAnaGabriela_Lab08ARSW-/blob/master/Imágenes/7-1090000.png)  

8. Dírijase ahora a Azure y verifique el consumo de CPU para la VM. (Los resultados pueden tardar 5 minutos en aparecer).

![](https://github.com/gabrielaasilva/SilvaAnaGabriela_Lab08ARSW-/blob/master/Imágenes/8.png)

9. Ahora usaremos Postman para simular una carga concurrente a nuestro sistema. Siga estos pasos.

![](https://github.com/gabrielaasilva/SilvaAnaGabriela_Lab08ARSW-/blob/master/Imágenes/9.png)


**Preguntas Parte 1**

1. ¿Cuántos y cuáles recursos crea Azure junto con la VM?
    - Virtual Network
    - IP
    - Interfaz de red
    - Security group
    - Disco
    
2. ¿Brevemente describa para qué sirve cada recurso?
    - **Virtual Network:** es el bloque de creación fundamental de una red privada en Azure. VNet permite muchos tipos de recursos de Azure, como Azure Virtual Machines (máquinas         virtuales), para comunicarse de forma segura entre usuarios, con Internet y con las redes locales. VNet es similar a una red tradicional que funcionaría en su propio             centro de datos, pero aporta las ventajas adicionales de la infraestructura de Azure, como la escala, la disponibilidad y el aislamiento.
    - **IP:** La dirección IP es el número que identifica de forma individual la conexión de un equipo o dispositivo a una red interna o externa. Sin una dirección de IP es               imposible que ningún dispositivo, sea un ordenador, un smartphone o gadget se conecte a Internet.
    - **Interfaz de red:** La capa de interfaz de red TCP/IP formatea los datagramas IP de la capa de red en paquetes que las tecnologías de red específicas pueden interpretar y transmitir.
    - **Security group:** filtra el trafico de red desde y para los recursos de Azure en una red virtual de Azure. Un grupo de seguridad se basa principalmente en un conjunto de reglas de seguridad que permiten o niegan el trafico de red entrante o el trafico de red saliente. 
    - **Disco:** Lugar donde se almacena el sistema operativo de la maquina virtual creada.

3. ¿Al cerrar la conexión ssh con la VM, por qué se cae la aplicación que ejecutamos con el comando `npm FibonacciApp.js`? ¿Por qué debemos crear un *Inbound port rule* antes de acceder al servicio?
- 
5. Adjunte tabla de tiempos e interprete por qué la función tarda tando tiempo.
6. Adjunte imágen del consumo de CPU de la VM e interprete por qué la función consume esa cantidad de CPU.
7. Adjunte la imagen del resumen de la ejecución de Postman. Interprete:
    * Tiempos de ejecución de cada petición.
    * Si hubo fallos documentelos y explique.
8. ¿Cuál es la diferencia entre los tamaños `B2ms` y `B1ls` (no solo busque especificaciones de infraestructura)?
9. ¿Aumentar el tamaño de la VM es una buena solución en este escenario?, ¿Qué pasa con la FibonacciApp cuando cambiamos el tamaño de la VM?
10. ¿Qué pasa con la infraestructura cuando cambia el tamaño de la VM? ¿Qué efectos negativos implica?
11. ¿Hubo mejora en el consumo de CPU o en los tiempos de respuesta? Si/No ¿Por qué?
12. Aumente la cantidad de ejecuciones paralelas del comando de postman a `4`. ¿El comportamiento del sistema es porcentualmente mejor?



**Preguntas Parte 2**

* ¿Cuáles son los tipos de balanceadores de carga en Azure y en qué se diferencian?, ¿Qué es SKU, qué tipos hay y en qué se diferencian?, ¿Por qué el balanceador de carga necesita una IP pública?
* ¿Cuál es el propósito del *Backend Pool*?
* ¿Cuál es el propósito del *Health Probe*?
* ¿Cuál es el propósito de la *Load Balancing Rule*? ¿Qué tipos de sesión persistente existen, por qué esto es importante y cómo puede afectar la escalabilidad del sistema?.
* ¿Qué es una *Virtual Network*? ¿Qué es una *Subnet*? ¿Para qué sirven los *address space* y *address range*?
* ¿Qué son las *Availability Zone* y por qué seleccionamos 3 diferentes zonas?. ¿Qué significa que una IP sea *zone-redundant*?
* ¿Cuál es el propósito del *Network Security Group*?
* Informe de newman 1 (Punto 2)
* Presente el Diagrama de Despliegue de la solución.




