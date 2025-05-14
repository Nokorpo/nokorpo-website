---
layout: post
title: "QA para indies: ejemplos y enlaces de referencia"
teaser: /assets/images/posts/qa-para-indies/portada.png
categories: blog
---

¡Nokorpo estuvo en Guadalindie! Nepo dió una charla sobre cómo aplicar técnicas de QA para mejorar la calidad de nuestros juegos. Este post tiene las slides y una recopilación de código, ejemplos y enlaces de referencia para ayudarte a empezar con el QA de tu juego.

Si necesitas ayuda con QA o automatización en tu equipo, [¡contáctanos!](#contacto)

![logo de Guadalindie, la feria de juegos indie del sur](/assets/images/posts/qa-para-indies/guadalindie-logo.png){:width="50%" style="display:block; margin-left:auto; margin-right:auto"}

### Slides

Haz click en la imagen que ves a continuación para descargar las slides:

<a href="/assets/downloads/guadalindie/guadalindie.pdf">
![una captura de la portada de la presentación, con título "QA para indies: deja de apagar fuegos y empieza a prevenir bugs"](/assets/images/posts/qa-para-indies/pdf.png)
</a>

Estas son las slides de la charla. Siempre dejo algunas notas en la sección de "speaker notes" para acordarme de que tengo que decir algo. Pero la información importante está visible en la slide.

### Tests de integración

La estructura típica para escribir un test de integración es:

* **GIVEN:** preparar variables, datos e instancias de clases que necesites para el test. Básicamente, configurar el contexto sobre el que el test se ejecutará.
* **WHEN:** realizas la acción que quieres testear. Esta tendrá cambios sobre el contexto que hemos montado.
* **THEN:** comprobamos que la acción genera los cambios que esperamos y que tiene el resultado que esperamos.

Un ejemplo de definición de un test podría ser:

```gherkin
Scenario: Player hit by ball
Given the player object
  And the ball object
When  the ball moves towards the player and hits it
Then  the player detects the hit
  And the player moves in the opposite direction from where the ball hit it
```

Y la implementación del mismo en GDScript, usando GUT:

```gdscript
func test_player_hit_by_ball() -> void:
	#GIVEN
	var test_scene: Node3D = add_child_autofree(_test_scene.instantiate())
	var player: Player = test_scene.find_child("Player")
	var original_player_position: Vector3 = player.global_position
	watch_signals(player)
	var ball: Ball = test_scene.find_child("Ball")

	#WHEN
	ball.velocity = Vector3(0, 0, 4)
	await(wait_for_signal(player.player_hit_by_ball, 2, "wait for hit"))
	# wait for hit animation to finish
	await(wait_for_signal(player.player_hit_ended, 2, "wait for hit"))
	
	#THEN
	assert_signal_emitted(player, "player_hit_by_ball", "player didn't receive hit")
	assert_almost_eq(player.velocity, Vector3(0, 5, 9), Vector3.ONE, "player was not pushed backwards")

```

### CI

En la charla hablé de los entornos de Integración Continua (CI, por las siglas en inglés). Aunque no pude entrar a explicarla en detalle, compartí la configuración de CI que usamos en jams. Esta hace la build web de un juego de Godot y la publicar directamente a Itch, todo con sólo pulsar un botón.

Puedes encontrar esa configuración [en el repositorio de nuestro juego de jam Infinigrass](https://github.com/Nokorpo/infinigrass/blob/main/.github/workflows/main.yml).

Para entender este fichero, preparé unas imágenes que traducen lo que está haciendo:

![Captura del fichero de configuración del CI de Michiball. Separo el fichero en 3 partes: la configuración de cuándo se ejecuta, la sección de variables y la sección de los pasos a seguir](/assets/images/posts/qa-para-indies/config_ci_01.png)
![Captura del fichero de configuración del CI de Michiball. Está enfocada la parte de los pasos a seguir. Los pasos están separados en 4 partes: descarga del repositorio, setup de godot, generar la build web, subirla a itch](/assets/images/posts/qa-para-indies/config_ci_02.png)

Si quieres más información sobre cómo configurar Github para usar este script, escribí un [post sobre cómo usarlo en mi blog](https://nepo.dev/posts/ci-config-para-jams.html). Es un tutorial para gente que esté usando un CI por primera vez, por lo que puedes usarlo para aprender más sobre cómo funciona un CI.

### GDSnap

Si queréis probar la herramienta de Screenshot testing para Godot que hemos creado, lo podéis hacer aquí: [GDSnap en Github](https://github.com/Nokorpo/GDsnap).

![imagen de diferencia entre 2 capturas generado por GDSnap](/assets/images/posts/qa-para-indies/player_selection_diff.png){:width="50%" style="display:block; margin-left:auto; margin-right:auto"}

Estamos pendientes de que lo acepten en la Asset Library de Godot. En cuanto lo revisen, añadiremos el enlace en este post.

Tiene licencia MIT, por lo que podéis hacer lo que queráis con el proyecto. Sería bonito ver que se hacen versiones para otros motores :)

### Recursos adicionales

Si os interesa informaros más sobre QA y testing, os dejo algunos enlaces que os pueden interesar:
- [Charla GDC: test automáticos en Sea of Thieves](https://www.youtube.com/watch?v=X673tOi8pU8)
- [Recopilación de recursos (charlas, artículos...) sobre testing automático](https://trello.com/b/nGE5yqZk/game-automated-testing-resource-hub)
- [Github Actions quickstart guide](https://docs.github.com/en/actions/writing-workflows/quickstart)

### Contacto

Y si necesitas ayuda configurando esto para tu equipo, ¡ponte en contacto!

* Email: [contact@nokorpo.com](mailto: contact@nokorpo.com)
* Mastodon: [@nokorpo@gamedev.lgbt](https://gamedev.lgbt/@nokorpo)
* Bluesky: [@nokorpo-dev.bsky.social](https://bsky.app/profile/nokorpo-dev.bsky.social)

