
# PRUEBA TÉCNICA TENPO


El presente documento describe una necesidad de software que debe ser implementada con el objetivo de validar los conocimientos del aspirante al cargo de **JAVA DEVELOPER**.
Se solicita la implementación de un Servicio Web **(REST o SOAP)** el cual permita gestionar un examen de selección múltiple con las siguientes funcionalidades:

### Necesidades
1.  Debes desarrollar una API REST en Spring Boot utilizando java 11 o superior, con las siguientes funcionalidades:

        a.  Debe contener un servicio llamado por api-rest que reciba 2 números, los sume, y le aplique una suba de un porcentaje que debe ser adquirido de un servicio externo (por ejemplo, si el servicio recibe 5 y 5 como valores, y el porcentaje devuelto por el servicio externo es 10, entonces (5 + 5) + 10% = 11). Se deben tener en cuenta las siguientes consideraciones:
            i.  El servicio externo puede ser un mock, tiene que devolver el % sumado.
            ii. Dado que ese % varía poco, se debe de garantizar que esa información expire cada 30 min.
            iii. Si el servicio externo falla, se debe devolver el último valor retornado. Si no hay valor, debe retornar un error la api.
            iv. Si el servicio falla, se puede reintentar hasta 3 veces.
        b.  Historial de todos los llamados a todos los endpoint junto con la respuesta en caso de haber sido exitoso. Responder en Json, con data paginada. El guardado del historial de llamadas no debe sumar tiempo al servicio invocado, y en caso de falla, no debe impactar el llamado al servicio principal.
        c.  La api soporta recibir como máximo 3 rpm (request / minuto), en caso de superar ese umbral, debe retornar un error con el código http y mensaje adecuado.
        d. El historial y la información de los usuarios se debe almacenar en una database PostgreSQL.
        e.  Incluir errores http. Mensajes y descripciones para la serie 4XX.

2.   Se deben incluir tests unitarios.
3.  Esta API debe ser desplegada en un docker container. Este docker puede estar en un dockerhub público. La base de datos también debe correr en un contenedor docker. Recomendación usar docker compose.
4.  Debes agregar un Postman Collection o Swagger para que probemos tu API.
5.  El código debe ser enviado adjunto por correo, no en un repositorio público, junto con las indicaciones de prueba.
6.  Tener en cuenta que la aplicación funcionará de la forma de un sistema distribuido donde puede existir más de una réplica del servicio funcionando en paralelo

### Restricciones
- Todos los métodos que se creen en el API deberán consumir JSON y producir JSON.
- La aplicación deberá ser implementada en lenguaje Java, por medio del Framework Spring Boot.
- Los datos deberán quedar persistidos en una base de datos que usted escoja (PostgreSQL).
- Las dependencias deben ser configuradas en Maven.
- Se debe implementar el código aplicando las buenas prácticas que considere.
### Entregables
- Código fuente de la aplicación (preferiblemente en un repositorio como GitHub).
- Script para la creación de la BD (en caso de que se necesite).
- Colección de las CURL para el consumo de los métodos que se definan en el API (se puede
utilizar Postman).


## 🚀 Acerca de mí...
• Soy una persona autodidacta, ágil, comunicativo, responsable, dedicado y proactivo, 
amante de la tecnología e innovador. siempre dispuesto a afrontar nuevos retos que 
me hagan crecer tanto personal como profesionalmente, Cuento con más de 1 año de 
experiencia como developer java.

• Actualmente e tenido la gran oportunidad de participar en más
de 3 proyectos importantes dentro de la organización junto con un gran
equipo de desarrolladores, donde me desempeño como desarrollador
Backend manejando lenguaje como Java, Spring Boot, Thymeleaf,
Microservicios, Postman, AWS, Bitbucket, Maven, Kafka, Mqtt, Base de datos
Sql, NoSql y despliegue en tomcat.


## Autor

- [@Github/wilsonevs](https://github.com/wilsonevs)
- [@Linkedin/wilsonevs](https://www.linkedin.com/in/wilsonvalencs/)
- [@Torre/wilsonevs](https://torre.co/wilson_evs)

# Instalación

1.  Dentro de la carpeta `Tenpo` se encuentra 2 proyectos que son los siguientes:
    - **`suma-wilson-tenpo`**: Es el proyecto principal
    - **`porcentaje-wilson-tenpo`**: Es el proyecto segundario (Externo)

2. Para levantar nuestro 2 proyectos antes debemos haer unos pasos posteriores:
    - **Paso 1**: Tener previamente, instalado docker, dejo el link de instalación [Docker](https://docs.docker.com/engine/install/)
    - **Paso 2**: Buscar archivo llamado **docker-compose.yml**
    - **Paso 3**: procedemos a levantar, el docker-compose, con el comando siguiente:
    ```
    docker-compose up -d --build
    ``` 
    - **Paso 4**: Una vez que las imágenes se instalen e inicialicen, procedemos a validar el primer puerto que nos muestra la imagen de Postgres. Para ello, debemos abrir una terminal e ingresar el siguiente comando, que nos permitirá mostrar todas las imágenes que están en UP:
    ```
    docker ps -a
    ``` 
     - **Paso 5**: Una vez obtengamos, el número del puerto, vamos a cada uno de nuestros proyectos y buscamos el archivo llamado application.properties
        - **`suma-wilson-tenpo`**: spring.datasource.url=jdbc:postgresql://localhost:**(Cambiar puerto)**/tenpo
        - **`porcentaje-wilson-tenpo`**: spring.datasource.url=jdbc:postgresql://localhost:**(Cambiar puerto)**/tenpo
    - **Paso 6**: procedemos a ejecutar nuestros 2 proyectos, en el cual debe ser en orden, primero **`porcentaje-wilson-tenpo`**  y luego  **`suma-wilson-tenpo`**.

## Acceder al Swagger
Se implemento para que pudiera vizualizar los Api de los proyectos:
- `suma-wilson-tenpo`: [suma-wilson-tenpo](http://localhost:8079/swagger-ui/index.html)
- `porcentaje-wilson-tenpo`: [porcentaje-wilson-tenpo](http://localhost:8078/swagger-ui/index.html)

## Acceder Postamen
Se debe importar el archivo llamado **Tenpo.postman_collection** de postaman


## Postgress
Una vez se inicialize Docker compose, podremos ingresar a la interfaz de pgadmin4 [Postgress](http://localhost/login) de la base de datos, donde nos va a pedir lo Email/Password.

- **Email:** wilsonev.saldarriaga88@gmail.com 
- **Password:** admin

### Servers
- **General**
  - **Name**: Tenpo
- **Connection**
  - **Host name/Addres:** postgres 
  - **Port:** 5432
  - **Username:** admin
  - **Password:** admin
  - **Name DB:** tenpo

# GUIA DEL CONSUMO
## **CURLS**
### Operators
Method: **GET**
Observacion: 
```JSON
  curl --location 'localhost:8079/operadores/get/operacion/?userid=clientuuid_345555' \
  --data ''
```

Method: **POST**
```JSON
curl --location 'localhost:8079/operadores/save/operacion/' \
--header 'xauth: wilson3042258679' \
--header 'Content-Type: application/json' \
--data '{
    "valueUno": 10,
    "valueDos": 2,
    "clientUuid": "clientuuid_345555"
}'
```
## UserHistory
Method: **GET**
```JSON
curl --location 'http://localhost:8079/history/get/list/operacion/1/12' \
--data ''
```
Method: **GET**
```JSON
curl --location 'http://localhost:8079/history/get/list/operacion/0/4/?clientuuid=clientuuid_f3eb5415-b25c-48d5-98fb-f57a9d3ee1ed_15%2F02%2F2023_02%3A58%3A00' \
--data ''
```
## Porcentaje
Method: **POST**
```JSON
curl --location 'http://localhost:8078/porcentaje/operacion/?client-id=clientuuid_dfda28f2-ef2d-4328-846f-fbb41dd96362_29%2F01%2F2023_15%3A16%3A25' \
--header 'api-auth: wilson3042258679' \
--header 'Content-Type: application/json' \
--data '{
  "valueSuma": 10.5,
  "porcentaje": 10.7
}'
```

| PARAMETRO         | TIPO      | VALOR     |
| :--------         | :-------  | :---------|
| `paginaActual`    | `int`     | `1`       |
| `paginacion`      | `int`     | `100`     |