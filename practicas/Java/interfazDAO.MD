# Interfaz DAO
La interfaz [DAO viene con su acrónimo que significa _"Data Access Object"_](https://es.wikipedia.org/wiki/Objeto_de_acceso_a_datos).
Este tipo de interfaces surgen de la necesidad de obtener datos de distintas fuentes que necesitan distintas implementaciones, pero usando un mismo comportamiento declarado en el interfaz DAO.

Se debe declarar la interfaz `EventoDAO` con los siguientes métodos tipicos de un CRUD:
1. `Collection<Evento> getEventos()`: devolverá todos los eventos.
1. `Collection<Evento> getEventos(Date fecha)`: devolverá todos los eventos para la fecha pedida
1. `boolean guardarEvento(Evento evento)`: almacenará el evento pasado. Devolverá `true` si la operación de guardado finalizó con éxito.
1. `Evento removeEvento(Evento evento)`: borrará el evento pasado. Devolverá el evento que ha borrado si se realizó el guardado con éxito.
1. `boolean actualizarEvento(Evento evento)`: actualizará el evento pasado. Devolverá `true` si la actualización finaliza con éxito.

```java
public interface EventoDAO {

    Collection<? extends Evento> getEventos();
    Collection<? extends Evento> getEventos(Date fecha);
    <T extends Evento> T boolean guardarEvento(T evento);
    <T extends Evento> T removeEvento(T evento);
    <T extends Evento> boolean actualizarEvento(T evento);
    
}
```

Esta interfaz se implementará total o parcialmente en los tipos que se hayan creado durante las prácticas de [Serialización](https://github.com/DptoSIC/DatosDeportivos/blob/master/practicas/Java/serializacion.MD#serializaci%C3%B3n) y las llamadas a los antiguos métodos serán substituidas por llamadas a través de la interfaz `EventoDAO`.
Se verán las diferencias al usar las distintas implementaciones de `EventoDAO`: CSV, JSON, Acceso a BD con SQL, Servicios Web, etc...
