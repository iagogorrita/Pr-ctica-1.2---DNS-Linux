# **SRI** :kissing_closed_eyes:
## Instalación de Apache+Virtual Host

### 1. DNS
Primero tendremos que añadir y configurar nuestro servidor DNS con una imagen BIND9, podremos ver como esta configurado en el docker-compose.
El codigo para crearlo será el siguiente:
```
  bind9:
    container_name: web_bind9
    image: ubuntu/bind9
    platform: linux/amd64
    networks:
      network:
        ipv4_address: 172.28.0.40
    ports:
      - '53:53/tcp'
      - '53:53/udp'
    volumes:
      - ./dns/conf/:/etc/bind/
      - ./dns/zones/:/var/lib/bind/
```
### 2. Ips fijas en los contenedores apache
Tendremos dos contenedores de apache con dos ips diferentes, 

