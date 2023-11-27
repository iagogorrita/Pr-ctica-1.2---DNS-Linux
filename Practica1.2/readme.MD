# **SRI** :kissing_closed_eyes:
## DNS Linux

###

Para crear un servidor DNS en Ubuntu será bastante diferente a crearlo en Docker ya que en docker tendremos que mapear puertos y volumenes, mientras que en el Ubuntu eso ya lo hará la instalación de Bind9 que es otra diferencia con el docker, para hacer la instalación de nuestro servidor DNS en Ubuntu haremos lo siguiente:

1. Tendremos que hacer un **`sudo apt install bind9`** que instalará el paquete bind9 para hacer nuestro servidor DNS, y justo después tendremos que instalar la herramienta para hacer dig haciendo un **`sudo apt install dnsutils`**, con esto ya tendriamos lo necesario para empezar con la configuración de nuestro DNS.


2. Los archivos para configurar el DNS estarán en /etc/bind/ que tendrá la configuración principal en el archivo **named.conf**, que tendrá dentro la disposición de los archivos de configuración del dns que serán los siguientes:
    - /etc/bind/named.conf.options: con las opciones globales del DNS
    - /etc/bind/named.conf.local: para configurar las zonas
    - /etc/bind/named.conf.default-zones: Las zonas predeterminadas como localhost.

3. La configuración predeterminada solo actuará como un servidor caché, que es un servidor que almacena localmente el contenido solicitado con frecuencia para acelerar el acceso y reducir el uso del ancho de banda. Para que cambiar esto, descomentaremos la linea de forwarders y pondremos los DNS que querramos.
    
    Después de cambiar esta configuración tendremos que utilizar el siguiente comando para que se aplique: **`sudo systemctl restart bind9.service`**
4. Para añadir una zona DNS a Bind9, para convertir a Bind9 en un 
