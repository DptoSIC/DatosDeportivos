# DatosDeportivos
Applicación y librerías para la carga y explotación de datos deportivos.

Servirá como proyecto integrador de varias asignaturas del curso para tener una visión amplia e integrada de competencias pertenecientes a distintas asignaturas del currículo y que será coordinado por la asignatura de Dirección de Proyectos.

# Descripción funcional
El resultado final deseado es una aplicación multidispositivo y multiplataforma que permita la extracción/obtención, almacenamiento, tratamiento, consulta, explotación y consumo de datos deportivos.

**Librería**
---
Deberá tener una parte común compartida por todos los servicios e interfaces de usuario que sean parte del proyecto (REST API, consola, desktop, mobile y web app) así como tener capacidad para admitir otras en un futuro (Voice User Interface o IoT por ejemplo).

**ETL**
---
Deberá ser capaz de extraer datos de las siguientes fuentes:
1. Descargas de datos en ficheros de texto plano: CSV, JSON, XML... (desde [football-data.co.uk](http://www.football-data.co.uk/data.php) por ejemplo).
1. Peticiones a servicios Web tipo REST API, SOAP,... (por ejemplo [football-data](https://www.football-data.org/))
1. Scrapper Web de páginas de resultados deportivos (como [XScores](https://www.xscores.com/), [iApuestas](http://www.iapuestas.com/es/)) o directamente casas de apuestas.

**Persistencia**
---
Deberá ser capaz de almacenar los datos según un modelo de datos común en los siguientes soporte:
1. Ficheros de texto plano (por ejemplo JSON).
1. BDs Relacional (Oracle, Access, etc...).
1. BDs NoSQL (Plataformas como [Firebase](https://firebase.google.com/) o Mongo DB,...).

**Backend**
---
Tendrá una REST API que suministrará los datos extraidos y otros que pueda generar para aumentar el rendimiento, adaptarse a su modelo de datos e integrar las distintas fuentes de datos. Esta REST API se programará en Java con Spring Framework.

Deberá tener definido el servicio en la OpenAPI Specification de [Swagger](https://swagger.io/).

**Frontend**
---
Tendrá varios Frontend, entre los cuales se verán:
1. Consola (Java y Firefox developer)
1. Desktop (Java)
1. Mobile (Android)
1. Web App

**Respecto a los datos que tratará:**
---
Al ser datos deportivos habrá que tener eventos deportivos. Estos eventos deportivos pueden tener cualquier número de participantes, no sólo partidos de futbol aunque los ejemplos que se hayan puesto y los que se trabajen en profundidad sean sobre este tipo de eventos entre dos contrincantes (debe estar preparado para atletismo, carreras de coches o incluso competiciones individuales para records).

Estos eventos se realizarán en una fecha y hora concretas y tendrán un resultado.

Los participantes en estos eventos deberán ser identificados de manera unívoca aunque las distintas fuentes de datos los identifiquen de formas distintas. Dependiendo del tipo de deporte podrán tener unos datos u otros, pero todos tendrán al menos un nombre.

Se llevará un control de los sucesos que ocurran durante el evento como goles, tarjetas, expulsiones, descalificaciones, retiradas, averias, lesiones, etc...

Se podrán hacer consultas adhoc, filtrar los resultados y ordenar por distintos criterios.

Se podrán tener estadísticas sobre aspectos concretos del juego calculados para eventos agrupados de una forma concreta (una jornada de liga, una competición completa, medias anuales, etc...).
