# Informe de Auditoría de Red Wi-Fi Insegura
**Auditor de Seguridad:** Mateo Bentos
**Proyecto:** Pre-entrega 6 - Ciberseguridad

## Introducción
Las redes Wi-Fi públicas en cafeterías o aeropuertos representan un riesgo crítico para la seguridad de la información. Compartir el "aire" con usuarios desconocidos abre la puerta a vulnerabilidades como la intercepción de datos (Sniffing), los ataques de intermediario (Man-in-the-Middle) y las redes gemelas malignas (Evil Twins). Este informe documenta los riesgos reales de navegar sin protección y demuestra la vulnerabilidad del tráfico en texto plano.

## Sitio analizado
* **Host:** `http://neverssl.com`

## Evidencia observada
Al analizar la conexión al sitio mencionado utilizando las herramientas de desarrollador del navegador (pestaña Network), se interceptó la solicitud inicial revelando la siguiente información expuesta en texto plano:
* **Protocolo utilizado:** HTTP (Hypertext Transfer Protocol). No utiliza HTTPS, lo que significa que la conexión carece de certificados de seguridad y cifrado.
* **URL solicitada:** `http://neverssl.com/`
* **Método HTTP:** `GET` (Solicitud para obtener el recurso de la página principal).
* **Host:** `neverssl.com`
* **User-Agent:** Queda expuesto el sistema operativo, su versión y el navegador web exacto que está utilizando el cliente (ej. Mozilla/5.0, Windows NT 10.0, Chrome).
* **Headers enviados:** Se exponen encabezados como `Accept-Language`, `Connection`, y el estado de caché, revelando detalles sobre la configuración del usuario.

## Riesgos encontrados
Al navegar mediante el protocolo HTTP desde una red Wi-Fi pública, no existe ninguna barrera de seguridad entre el dispositivo del usuario y el router. El riesgo principal es que cualquier atacante conectado a la misma red puede utilizar herramientas de monitoreo (como Wireshark) para capturar los paquetes de red. Debido a que la información viaja en texto plano, el atacante puede interceptar credenciales (usuarios y contraseñas), robar cookies de sesión (secuestro de cuenta), y leer mensajes o datos personales exactamente como fueron enviados.

## Cómo ayuda una VPN
Frente a una red pública e insegura, una VPN (Virtual Private Network) cambia radicalmente el escenario defensivo garantizando la **privacidad** del usuario y la **protección del tráfico**. 
La VPN logra esto estableciendo un **túnel** virtual seguro entre el dispositivo y el servidor de destino mediante el **encapsulamiento** de los paquetes de datos. A todo este tráfico se le aplica un fuerte **cifrado** criptográfico; por lo tanto, aunque un atacante logre interceptar los paquetes en la cafetería, solo verá ruido aleatorio e ilegible, protegiendo completamente la integridad y confidencialidad de la información.

## 3 Reglas de Oro para redes Wi-Fi públicas
1. **Evitar operaciones críticas:** Nunca ingreses credenciales, datos bancarios ni realices compras online mientras estés conectado a una red pública abierta.
2. **Utilizar siempre una VPN:** Enciende tu red privada virtual (VPN) antes de comenzar a navegar para asegurar que todo tu tráfico viaje cifrado y dentro de un túnel seguro.
3. **Verificar HTTPS y apagar el Wi-Fi automático:** Asegúrate de que los sitios que visitas tengan el candado de seguridad (HTTPS) y configura tu teléfono/computadora para que no se conecte automáticamente a redes abiertas conocidas.
