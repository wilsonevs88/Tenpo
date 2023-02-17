
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

## Instalación

1.  Dentro de la carpeta `Tenpo` se encuentra 3 proyectos que son los siguientes:
    - **`lib-wilson-tenpo`**: Es una libreria donde se almacena los models, status y exception de los proyectos en general
    - **`suma-wilson-tenpo`**: Es el proyecto principal
    - **`porcentaje-wilson-tenpo`**: Es el proyecto segundario (Externo)

2.  Los 3 proyectos debemos generar .jar en este orden: primero **`lib-wilson-tenpo`**, seguidos **`suma-wilson-tenpo`** y por ultimo **`porcentaje-wilson-tenpo`**. para generar sus respectios .jar dejo las siguientes comandos:
    -   Opción 1 (Eclipse):
        ```
        Maven build...
        ```
    -   Opción 2 (IntelliJ IDEA):
        ```
        mvn clean install
        mvn clean package
        ```
        **`Nota`**
        ```
        Si por algun motivo, los proyectos no le estan permitiendo empaquetarlo, o sale algun error que no le permite continuar, como ultimo recurso debes dirigirte a la carpeta .m2 que por lo general se encuentra dentro del usuario de nuestro equipo de forma oculta. debes ingresar dentro de esta y borrar el archivo `repository`, y volver a realizar los pasos anteriores.
        ```

3.  Dentro de la carpeta Tenpo, se encuentra un archivo llamado **docker-compose.yml** que es el encargado de ejecutar los dos proyectos, solo debe levantarlo, con el siguiente comando:
    ```
    docker-compose up -d --build
    ```

## Acceder al Swagger
Se implemento para que pudiera vizualizar los Api de los proyectos:
- `suma-wilson-tenpo`: [Swagger](http://localhost:8081/swagger-ui/index.html)
- `porcentaje-wilson-tenpo`: [Swagger](http://localhost:8082/swagger-ui/index.html)


## Postgress
Una vez se inicialize Docker compose, ingresamos a la interfaz de pgadmin4 http://localhost/login de la base de datos, donde nos va a pedir lo Email/Password.

- **Email:** wilsonev.saldarriaga88@gmail.com 
- **Password:** admin

### Servers
- **General**
  - **Name**: ConnectionTenpo
- **Connection**
  - **Host name/Addres:** postgres 
  - **Port:** 5432
  - **Username:** admin
  - **Password:** admin
  - **Name DB:** tenpo


## API Referencía
##Nota 
* Primero se insertar las preguntas

* Segundo en el servicio del estudiante ingresa los datos y las preguntas


## GUIA DEL CONSUMO

#### Get - Busqueda completa


Ejemplo de como se debe consumir en Postman, 

Todos los servicios del GET se crearón con paginacionasi que debe ingresar lo siguiente
```http
  GET http://localhost:8089/fonYou/api/estudiante/?paginaActual=1&paginacion=100
  GET http://localhost:8089/fonYou/api/pregunta/usuario/?paginaActual=1&paginacion=100
  GET http://localhost:8089/fonYou/api/respuesta/?paginaActual=1&paginacion=100
```

| PARAMETRO         | TIPO      | VALOR     |
| :--------         | :-------  | :---------|
| `paginaActual`    | `int`     | `1`       |
| `paginacion`      | `int`     | `100`       |

#### Get - Busqueda por ID

```http
  GET http://localhost:8089/fonYou/api/estudiante/1
```

#### Post

```http
  POST http://localhost:8089/fonYou/api/estudiante/
```

```JSON
{
  "nombre": "Wilson Valencia 2",
  "edad": "33",
  "ciudad": "Medellín",
  "zona_horaria": "2022/03/26 22:00:00",
  "respuesta": [
    {
      "id_pregunta": 1,
      "respuesta": "a"
    },
    {
      "id_pregunta": 2,
      "respuesta": "b"
    },
    {
      "id_pregunta": 3,
      "respuesta": "a"
    }
  ]
}
```

#### Put

```http
  PUT http://localhost:8089/wilsonevs/api/estudiante/
```

```JSON
{
  "id_estudiante": 1,
  "nombre": "Wilson Valencia 2",
  "edad": "33",
  "ciudad": "Medellín",
  "zona_horaria": "2022/03/26 22:00:00",
  "respuesta": [
    {
      "id_pregunta": 1,
      "respuesta": "a"
    },
    {
      "id_pregunta": 2,
      "respuesta": "b"
    },
    {
      "id_pregunta": 3,
      "respuesta": "a"
    }
  ]
}
```


#### DELETE - Eliminación por ID

```http
  DELETE http://localhost:8089/fonYou/api/estudiante/1
