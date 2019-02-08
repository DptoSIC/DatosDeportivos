# Primeros pasos

Como checklist para saber si vas dando todos los pasos para ir construyendo la aplicación puedes usar la siguiente lista:
1. Haz un boceto con el modelo de datos donde tendrán que aparecer las entidades: `Evento`, `Participante`, `Suceso`, etc... No tengas miedo en poner todo lo que se te ocurra, ya se verá como queda al final.
1. Centrate en las entidades `Evento` y `Participante`. Son las primeras que necesitamos para manejar los datos, el resto apárcalas por ahora.
1. Descárga un fichero .CSV desde una web. Recomiendo bajar la [liga española de una temporada terminada](http://www.football-data.co.uk/spainm.php). La descarga viene con encabezado.
1. En la misma página hay un archivo que dice qué es cada campo del CSV.
1. Crea la clase `Evento` y deserializa los datos del CSV para crear objetos de ese tipo:
   1. Puede servirte inicialmente con 4 campos de tipo `String` para `local`, `visitante`, `fecha` y `resultado`.
   1. Para leer un fichero usa el [código de mi blog](https://hijosdelspectrum.blogspot.com/2019/02/leer-y-guardar-texto-en-un-fichero.html).
   1. En la línea de código que sirve para hacer algo con la línea leída con el buffer, tendrás que dividirla por el caractar de separación (porque es un CSV). Usa `String.split(carácter)` y tendrás un `String[]` con un campo en cada posición del array.
   1. Desde este momento debes coger sólo los datos que te interesan (local, visitante, fecha y resultado).
   1. Con esos cuatro valores instancia un objeto de tipo `Evento`.
   1. Cada objeto creado añádelo a una `Collection<Evento>` para ir recogiendo todos los eventos.
1. Ahora que ya tiene todos los eventos en memoria imprímelos para asegurarte que están leidos correctamente. Personaliza el `toString()` para ver quñe datos encapsula cada evento.
1. Lo siguiente será mejorar la clase `Evento`. En vez de tener cuatro atributos `String` haz que sean dos atributos tipo `Participante` para local y visitante. Repite la deserialización para ver que eres capaz de contruir objetos correctamente ahora que debes construir también participantes (por ahora sólo tiene un campo nombre) para los atributos de ese tipo.
1. Cambia el atributo `String fecha` por `Date fecha`. Para convertir de `String` a `Date` y viceversa utiliza la clase [`SimpleDateFormat`](https://docs.oracle.com/javase/8/docs/api/java/text/SimpleDateFormat.html). Repite que todo sigue correcto.
1. Si has llegado hasta aquí, ya tienes una clases con un resultado aproximado a lo que queremos lograr. Es el momento de guardar estos datos a disco en nuestro propio formato con un formato JSON:
   1. Utiliza la librería [`jsonbeans`](https://github.com/EsotericSoftware/jsonbeans#jsonbeans) para pasar un objeto en memoria a texto plano en formato JSON con el método `Json.toJson(evento)` que te devuelve un `String` con el evento pasado serializado a JSON.
   1. Imprímete esa cadena con el evento serializado para asegurarte que los datos son correctos. Observa que `fecha` está vacío.
   1. Practica una serialización más avanzada con la [práctica de serialización](https://github.com/DptoSIC/DatosDeportivos/blob/master/practicas/Java/serializacion.MD#serializaci%C3%B3n).
