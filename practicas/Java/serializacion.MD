# Serialización

`Evento` tendrá la estructura JSON siguiente:
```javascript
{
  "local":"[idLocal]",
  "visitante":"[idVisitante]",
  "sucesos":[
      // array de sucesos
    ],
  "fecha":{
    "dia":"[dd/MM/yyyy]",
    "hora":"[HH:mm]"
    }
}
```

Se practicará la serialización de `fecha` de dos formas:
1. Implementando un serializador personalizado de tipo `JsonSerializer<Date>`
1. Mediante el diseño y marcado de los atributos:
   * Se definirá una interfaz `Datable` que será implementada por `Evento` (directamente o heredando de `DatableImpl`)
   * Se marcarán con `transient` los atributos que no se deben serializar
   * Se implementará en los getters y setters la lógica para el control en los cambios de fechas

Se definirá una interfaz `Identificable`:
1. Tendrá el método `T getIdentificador()`. Para `Participante` `T` será de tipo `String`.
1. Se establecerá un gestor de participantes para no crearlos por duplicado.
1. Evento sólo guardará los `id`s para `local` y `visitante`
1. Al invocar a `getLocal/Visitante()` debe devolver el tipo `Participante` con todos los datos.
