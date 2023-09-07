# Apigateway Satellite
Punto único de acceso para cada satelite

Puerta de enlace/apigateway (nginx)

Contiene las [Reglas](nginx.conf) que redirigen las correspondientes solicitudes hacia los servicios privados
jwtAuth y RouterSatellite

La nomenclatura es {SATELLITE_NAME}.apigateway
Ejemplo kenobi.apigateway-skywalker.apigateway-sato.apigateway

# Tabla de contenido

- [Análisis y Diseño](Readme2.md)
- [Instalación](#instalación)
- [Construir_contenedor_para-ejecutar_en_un_satelite](#construir-contenedor-para-ejecutar-en-un-satelite)
- [Referencia de_Microservicios](#referencia-de-microservicios)

## Instalación

Clonar el repositorio en tu máquina local

```bash
git clone git@github.com:knvelasquez/apigateway.git
```

## Navegar hasta el directorio del proyecto

```bash
cd apigateway/
```

## Construir contenedor para ejecutar en un satelite

```bash
docker compose -f docker-compose.gateway.yaml up
```

### Esperar que finalice la creación de contenedores y la ejecución de pruebas
✔ Container jwt-auth            Created

✔ Container kafka               Created

✔ Container kenobi-api-gateway  Created

```bash
docker ps
```
**Output**
```bash
CONTAINER ID   IMAGE                                 COMMAND                  CREATED              STATUS          PORTS                                       NAMES
f092376d536b   bitnami/kafka:latest                  "/opt/bitnami/script…"   About a minute ago   Up 16 seconds   0.0.0.0:9092->9092/tcp, :::9092->9092/tcp   kafka
a92d049f0ba3   knvelasquez/routersatellite:v1.1      "/usr/local/bin/mvn-…"   About a minute ago   Up 16 seconds                                               router-satellite
4079cb7bace8   bitnami/zookeeper:latest              "/opt/bitnami/script…"   2 minutes ago        Up 17 seconds   2181/tcp, 2888/tcp, 3888/tcp, 8080/tcp      zookeeper
c44e5943f469   knvelasquez/coordinateresolver:v1.1   "/usr/local/bin/mvn-…"   2 minutes ago        Up 17 seconds   0.0.0.0:9093->9093/tcp, :::9093->9093/tcp   coordinate-resolver
765658534f80   knvelasquez/jwtauth:v1.2              "/usr/local/bin/mvn-…"   6 hours ago          Up 17 seconds                                               jwt-auth
```


## Referencia de Microservicios
- [jwtAuth](https://github.com/knvelasquez/jwtauth)
- [RouterSatellite](https://github.com/knvelasquez/routersatellite)