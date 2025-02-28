---
layout: post
title: "Postmortem: Spain, Where Talent Ignites"
teaser: /assets/images/posts/spain-where-talent-ignites/teaser.jpg
categories: blog
---

En Nokorpo hemos hecho un videojuego para el [ICEX](https://www.icex.es/), una empresa pública con sede en Madrid que busca promover la internacionalización de las empresas españolas.

En el ICEX han lanzado la campaña _[«Spain, Where Talent Ignites»](https://spainwheretalentignites.com/)_ para promocionar la industria audiovisual española. La productora [Canada](https://www.canadacanada.com/) había hecho un corto llamado _[«La Causa Del Accidente Que Provocó El Incendio»](https://www.canadacanada.com/project/icex-la-causa)_, nos han contratado para hacer un videojuego.

El [videojuego puede jugarse en su web](https://spainwheretalentignites.com/game/), y el código fuente [está publicado como software libre en GitHub](https://github.com/Nokorpo/el-accidente).

## Cómo nos presentamos a la licitación

Nos llegó [el anuncio de la licitación](https://www.dev.org.es/en/noticias-a-eventos/noticias-dev/640-icex-lanza-una-concurso-para-la-creacion-de-un-mini-videojuego-para-la-campana-spain-where-talent-ignites) y dedicamos unos días a preparar una propuesta de videojuego que les pudiese gustar.

Nuestra diseñadora [Alicia Redondo](https://www.linkedin.com/in/aliciaredmarr/) estuvo diseñando la jugabilidad del juego:

![Diagramas y dibujos explicando el diseño del videojuego](/assets/images/posts/spain-where-talent-ignites/design.jpg)

Y nuestra artista [Helena Cabanillas](https://es.linkedin.com/in/helena-cabanillas-serrano-63085b21b) ilustró algunos concepts de cómo sería el estilo artístico:

![Concept arte sobre cómo se vería el videojuego, aparece un personaje de dibujos 2D corriendo sobre unas plataformas](/assets/images/posts/spain-where-talent-ignites/screenshot.jpg)

[Nepo](https://nepo.dev/) estuvo valorando la viabilidad técnica, ya que pedían un juego web que funcionase en PC y en navedores móviles para iOS y Android, y [Pablo Rubio](https://antimundo.es/) revisó mucha burocracia, contratos, y otos papeles aburridos y fijó un **presupuesto de 10.000€** para nuestro proyecto, sobre el **presupuesto máximo de 14.750€** que había disponible.

### Nuestro proyecto es elegido

Lo cierto es que **al principio teníamos pocas esperanzas de que fuesen a elegir nuestra propuesta**, el anuncio del ICEX lo había visto mucha gente y dimos por hecho que se presentarían muchos equipos con grandes propuestas.

Sin embargo, nos sorprendimos cuando unos días después se nos contactó, estuvimos en una reunión donde nos preguntaron dudas sobre nuestra propuesta, y al día siguiente **nos confirmaron que habíamos sido seleccionados**.

Sobre el por qué, nos dijeron que nuestra propuesta estaba trabajada y nos habíamos detenido en hacerla a medida para su proyecto. Probablemente también influyó mucho el trabajo de nuestra artista, que hizo que el juego entrase bien por los ojos.

![Concepta art del videojuego, aparece un coche de dibujos por una escena en un estudio de cine en llamas](/assets/images/posts/spain-where-talent-ignites/screenshot-2.jpg)

## Manos a la obra, cómo fue hacer el juego

El desarrollo fue muy rápido debido a que querían el juego para antes de navidad y el proyecto empezó el 2 de diciembre. Además, nos suponía un reto adicional porque teníamos trabajos de otros clientes simultáneamente, así que tuvimos que organizarnos bien y trabajar con eficiencia.

Estuvimos involucradas cinco personas en el proyecto:

- [Alicia Redondo Martos](https://linktr.ee/alicia.redmarr): Game design.
- [Helena Cabanillas Serrano](https://www.linkedin.com/in/helena-cabanillas-serrano-63085b21b/): Arte.
- [Juan Antonio (Nepo) Nepormoseno Rosales](https://nepo.dev/): Programación y QA.
- [Sara Krikech Alcalde](https://krikeshh.com/): Soporte de 2DFX.
- [Pablo (Antimundo) Rubio Ruiz-Ayúcar](https://antimundo.es/): Producción.

### Integración continua

Para poder probar el juego desde móvil y pasárselo a testers, Nepo preparó un entorno de integración continua, que generaba builds del juego automáticamente y las subía a una web que podíamos compartir con quien quisieramos probar el juego.

![Captura de pantalla del entorno para publicar builds del juego en el CI en GitHub](/assets/images/posts/spain-where-talent-ignites/ci.jpg)

### Diseño móvil

Un reto que tuvimos, es que el juego debía funcionar en **navegadores de dispositivos móviles** y se jugaba con el móvil en horizontal _(o landscape)_, sin embargo la mayoría de personas usamos el móvil en vertical _(o portrait)_.

**El juego debía poner la imágen del móvil en horizontal automáticamente**, sin embargo algunos navegadores bloquean que las webs puedan rotar la pantalla, además muchos usuarios tienen activado el bloqueo de rotación, por lo que tuvimos que diseñar una pantalla que detectase la orientación del móvil y pidiese al usuario rotarlo, o le permiteise jugar de todas formas aunque no gire el móvil.

![Captura de pantalla del videojuego cuando pide al jugador que rote la pantalla](/assets/images/posts/spain-where-talent-ignites/rotate.jpg)

### Apartado artístico

Helena Cabanillas hizo un trabajo fantástico en este apartado, y contamos con la ayuda de Sara Krikech para hacer 2DFX.

<div class="img-container">
    <img src="/assets/images/posts/spain-where-talent-ignites/end-screen.jpg" alt="Ilustración de un coche estrellado contra un árbol en llamas">
    <img src="/assets/images/posts/spain-where-talent-ignites/animations.gif" alt="Collage de las animaciones de los personajes del juego">
    <img src="/assets/images/posts/spain-where-talent-ignites/main-menu.jpg" alt="Ilustración de un personaje en un aparcamiento al amanecer">
</div>
<div class="img-container">
    <img src="/assets/images/posts/spain-where-talent-ignites/sticker-1.gif" alt="GIF del personaje de Berta Prieto">
    <img src="/assets/images/posts/spain-where-talent-ignites/sticker-2.gif" alt="GIF del personaje de Berta Prieto">
    <img src="/assets/images/posts/spain-where-talent-ignites/sticker-3.gif" alt="GIF de un posit con un dibujo en el que aparece un coche estrellado contra un árbol en llamas">
</div>

### Diseño del juego

Decidimos hacer un juego de género runner porque nos pareció que la jugabilidad encajaba con la visión del corto. Replica la huída hacia adelante de Berta al no poder dejar de correr. La mecánica principal consiste en pulsar la pantalla para frenar, lo cual hace eco del miedo a no encontrarle un sentido al final del corto que frena a Berta ante sus dudas.

El proceso de creación de niveles fue el más iterativo. Una de las dificultades que tuvimos fue conseguir que los jugadores aprendan a frenar y soltar en el momento adecuado. Para eso colocamos las plataformas de los primeros “saltos” a una altura más baja. De esta forma las jugadoras las alcanzan con mayor facilidad y se acostumbran a la distancia del impulso. Y como hay muchos checkpoints, cada fallo supone una oportunidad para mejorar el manejo.

<div class="img-container">
    <img src="/assets/images/posts/spain-where-talent-ignites/screenshot-4.jpg" alt="Captura de pantalla del videojuego, aparece un coche de dibujos por una escena en un estudio de cine en llamas">
    <img src="/assets/images/posts/spain-where-talent-ignites/screenshot-3.jpg" alt="Captura de pantalla del videojuego, aparece un coche de dibujos estrellado contra un árbol en llamas">
    <img src="/assets/images/posts/spain-where-talent-ignites/screenshot-5.jpg" alt="Captura de pantalla del videojuego, aparece un personaje de dibujos corriendo por unas plataformas">
</div>

## El proyecto es software libre

Hemos propuesto al ICEX liberar este videojuego como software libre, y les ha parecido bien.

Los derechos de la propia campaña de _«Spain Where Talent Ignites»_ y del corto de _«La Causa Del Accidente Que Provocó El Incendio»_ son propiedad intelectual del ICEX, pero [el videojuego está publicado en GitHub bajo licencia MIT](https://github.com/Nokorpo/el-accidente) y es totalmente libre para que puedas estudiar el código y reutilizarlo en otros proyectos.

En Nokorpo creemos en el software libre por muchos motivos. Reduce los costos de desarrollo, fomenta la innovación y permite que los equipos desarrollen proyectos cada vez mejores con menos esfuerzo. Al hacer este juego libre permitimos que otros desarrolladores pueden aportar mejoras al juego, corregir errores, y estudiarlo en el futuro.

¡Además el juego está hecho en Godot 4 que es a su vez software libre!

![Un conejo imagen de marca de Nokorpo y el robot de Godot dándose la mano](/assets/images/services/godot.png)
