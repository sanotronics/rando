# Rando

Armá equipos de fútbol parejos para jugar con amigos, sin pensarlos vos.

El nombre viene de *random*: Rando prueba todas las divisiones posibles, se queda con las que dejan a los dos equipos parejos y elige una al azar. Así no salen siempre los mismos equipos.

Es una página web que anda en el celular. No hay que instalar nada, no hay cuentas y no usa ningún servidor.

## Qué hace

- **Puntajes que salen de una encuesta.** Cada jugador puntúa a los demás desde su celular. Rando combina todas las respuestas, así el puntaje de cada uno depende de lo que piensa el grupo y no de lo que opina una sola persona.
- **Equipos parejos y distintos cada semana.** Elige al azar entre las divisiones que quedan dentro de una diferencia máxima que definís vos.
- **Para pasar por WhatsApp o Telegram.** Los equipos salen en un mensaje listo para mandar, con el puntaje de cada equipo.
- **Historial.** Guardás cada partido y anotás el resultado.

## Cómo se usa

### Cargar a los jugadores

En la pestaña **Jugadores** podés pegar la lista entera, uno por línea y con o sin puntaje:

```
Pato 7,5
Colo 6
Rulo
```

El puntaje manual sirve para arrancar. A medida que lleguen respuestas de la encuesta, pesa cada vez menos.

### Hacer la encuesta

1. En **Encuesta**, tocá *Nueva encuesta*, elegí quiénes entran y qué se puntúa, y escribí tu WhatsApp como lo marcás (por ejemplo `11 2345-6789`).
2. Tocá *WhatsApp* o *Telegram* y mandá el link al grupo.
3. Cada uno abre el link, elige su nombre, marca a los que no conoce, puntúa del 1 al 10 y toca *Enviar por WhatsApp*. Eso te manda un mensaje con un código.
4. Volvé a **Encuesta**, pegá los mensajes (podés pegar el chat entero) y tocá *Cargar respuestas*.

Los jugadores no instalan nada: abren el link y listo.

### Armar los equipos

1. En **Partido**, elegí quiénes juegan (de 4 a 22).
2. Tocá *Armar equipos*. Si no te convence, *Otra opción*.
3. Para cambiar a alguien a mano, tocalo y después tocá a quien pasa al otro equipo.
4. Mandá el resultado por WhatsApp o Telegram, o copialo.
5. *Guardar* lo suma al historial.

La fecha del partido está arriba. Tocala para cambiarla.

## Qué se puntúa

Por defecto son cuatro atributos: **Técnica**, **Físico**, **Juego** y **Morfón**. En **Ajustes** podés cambiarlos, agregar otros o quitarlos, y elegir cómo se usa cada uno:

- **Suma al nivel:** la nota entra en el puntaje de cada jugador, que es lo que se compara para que los equipos queden parejos. Tiene un *peso*: 1 es lo normal y 2 cuenta el doble.
- **Se reparte parejo:** la nota no cambia el puntaje del jugador. Al armar los equipos se cuida que los dos tengan un promedio parecido en eso. Sirve para cosas como el morfón, para que no queden todos del mismo lado.

## Cómo se calculan los puntajes

- Se corrige a quien puntúa a todos alto o a todos bajo, aunque cada uno haya puntuado a jugadores distintos.
- En cada jugador se descartan las notas más extremas cuando hay suficientes, para que un rencor o una amistad no pesen de más.
- Con menos de 3 evaluaciones, el puntaje se apoya en el puntaje manual (que pesa como dos evaluaciones) o en el promedio del grupo, y se muestra en gris.
- Los puntajes manuales viejos se llevan a la escala de la encuesta.

## Cómo se arman los equipos

Se prueban todas las divisiones posibles (con 10 jugadores son 126). Entre las que quedan dentro de la diferencia máxima (por defecto 0,10) se elige una al azar, dando prioridad a las que reparten mejor los atributos. Además:

- Si marcás arqueros fijos, se reparten uno por equipo.
- Se evita repetir casi igual el último partido.
- Si ninguna división entra en el umbral, sale la más pareja.

## Privacidad

- Todo lo que cargás (jugadores, puntajes, partidos) queda en el navegador de tu celular. No se sube a ningún servidor ni al repositorio.
- El link de la encuesta lleva los nombres de los jugadores después del `#`, una parte que el navegador no le manda al servidor.
- La app no muestra los puntajes que puso cada uno, solo el resultado combinado.
- El único pedido externo es a Google Fonts, para cargar la tipografía. Si no hay conexión, usa una letra del sistema.
- Con el ojo de arriba podés ocultar los puntajes de los jugadores en la pestaña **Jugadores**.

## Publicarla

Es un solo archivo, `index.html`, así que se publica con GitHub Pages:

1. Creá un repositorio público llamado `rando` y subí el `index.html` a la raíz.
2. En **Settings → Pages**, elegí *Deploy from a branch*, rama `main`, carpeta `/ (root)`.
3. En un minuto queda en `https://<tu-usuario>.github.io/rando/`.

Los links de la encuesta solo funcionan desde la página publicada. En una vista previa o abriendo el archivo suelto, Rando te lo avisa y no te deja crearlos.

Para actualizarla, subí el nuevo `index.html`. La primera vez, recargá sin caché.

## Datos y copias de seguridad

- Los datos viven en un solo navegador. Usá siempre el mismo celular para organizar.
- Las respuestas de una encuesta se cargan en el mismo navegador donde la creaste.
- En **Ajustes → Descargar copia** bajás todo en un archivo, y con *Restaurar copia* lo pasás a otro dispositivo. No subas esa copia al repositorio: tiene los nombres y puntajes de tu grupo.

## Problemas comunes

| Qué pasa | Qué hacer |
| --- | --- |
| El link de la encuesta no abre | Crealo desde la página publicada, no desde una vista previa ni desde el archivo suelto. |
| WhatsApp abre un chat equivocado | Revisá el número en el formulario: Rando muestra a cuál va a abrir. Si es de otro país, empezalo con `+`. |
| Faltan los datos | Estás en otro navegador, o en una pestaña privada. Restaurá una copia. |
| Cargué un código y dice que es de otra encuesta | Cargalo en el navegador donde creaste esa encuesta. |
| No se ve la tipografía | Sin conexión se usa la letra del sistema. Es normal. |

## Desarrollo

No hay nada para compilar ni instalar: todo está en `index.html` (HTML, CSS y JavaScript, sin dependencias).

Para probarla en tu compu:

```bash
python3 -m http.server 8000
# abrí http://localhost:8000
```

Así anda todo, pero los links de la encuesta solo abren en esa misma computadora.

El código está ordenado en este orden: utilidades, estado, cálculo de puntajes, armado de equipos, códigos de la encuesta, interfaz y acciones.
