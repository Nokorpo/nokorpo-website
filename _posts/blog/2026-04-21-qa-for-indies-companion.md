---
layout: post
title: "QA for indies: slides, examples and references"
teaser: /assets/images/posts/qa-for-indies/portada.png
categories: blog
---

We're so happy for being able to give a talk at GodotCon! We talked about how to use the QA mindset to improve the quality of our games. The goal was to help indie/beginner teams without a lot of resources. This post containes slides, code samples and references links to help you start doing QA for your game.

If you need help with QA, automation or making your game, [contact us!](#contact)

![GodotCon Amsterdam logo](/assets/images/posts/qa-for-indies/godot_tulip_min.svg){:width="50%" style="display:block; margin-left:auto; margin-right:auto"}

### Slides

Click the following image to download a copy of the talk slides:

<a href="/assets/downloads/godotcon/slides.pdf">
![the title of the slides, it says "QA and Automation: Make a Better Game and Save Time + Money Doing It"](/assets/images/posts/qa-for-indies/pdf.png)
</a>

### Integration tests

The basic structure to write an integration test is:

* **GIVEN:** prepare variables, data and instances to classes/nodes you need for the test. In other words, configure the context in which the test will run
* **WHEN:** execute an action to generate the changes you want to test
* **THEN:** check the classes and nodes changed like you expected they would change

An example test definition could be:

```gherkin
Scenario: Player hit by ball
Given the player object
  And the ball object
When  the ball moves towards the player and hits it
Then  the player detects the hit
  And the player moves in the opposite direction from where the ball hit it
```

And the implementation for that test in GDScript, using [GUT](https://github.com/bitwes/Gut):

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

### Continuous Integration

In the talk I mentioned Continuous Integration environments (CI). I couldn't go into detail to explain how it works, but I shared the CI configuration we use for jam games. It generates a web build for a Godot game and publishes it on Itch, just by pressing a button.

You can find this configuration [in the repository of our jam game Infinigrass](https://github.com/Nokorpo/infinigrass/blob/main/.github/workflows/main.yml).

To understand this file, we prepared some images that translate what it's doing:

![Screen capture of a CI configuration file. Its content is split in 3 parts: configuration for when this CI job runs, a section for data and variables, and a section for the steps to follow](/assets/images/posts/qa-for-indies/config_ci_01.png)
![Screen capture of a CI configuration file. It shows the steps to follow. The steps are split in 4 parts: download the repository, setup Godot, generate the web build, upload it to itch](/assets/images/posts/qa-for-indies/config_ci_02.png)

If you want more information about how to configure Github to use this script, I wrote a [blog post about how to use it in my blog](https://nepo-dev.translate.goog/posts/ci-config-para-jams.html?_x_tr_sl=es&_x_tr_tl=en&_x_tr_hl=en). This is a tutorial for people using a CI for the first time, so you can use it to learn more about how a CI environment works!

There's a second blog post in the series which goes more into detail about [Docker concepts like images and containers](https://nepo-dev.translate.goog/posts/ci-config-para-jams-2.html?_x_tr_sl=es&_x_tr_tl=en&_x_tr_hl=en). Still want to know more? Check it out!

### GDSnap

If you want to try the Screenshot Testing tool we made, you can do so here: [GDSnap in Github](https://github.com/Nokorpo/GDsnap).

![a screen capture showing the difference between 2 game screenshots](/assets/images/posts/qa-para-indies/player_selection_diff.png){:width="50%" style="display:block; margin-left:auto; margin-right:auto"}

You can also find it in [Godot's Asset Library](https://godotengine.org/asset-library/asset/4018). Or you can download it directly from the editor, in the AssetLib section.

It has an MIT license, so you can do whatever you want with it. We'd love to see people extending it, writing issues or even creating versions for other engines! :)

### Additional resources

If you want to know more about QA and testing, I'll leave some links you might be interested in:
- [GDC talk: automated testing in Sea of Thieves](https://www.youtube.com/watch?v=X673tOi8pU8)
- [Resource compilation (talks, articles...) about automated testing](https://trello.com/b/nGE5yqZk/game-automated-testing-resource-hub)
- [Github Actions quickstart guide](https://docs.github.com/en/actions/writing-workflows/quickstart)
- Test runners mentioned:
    - [GUT by Butch Wesley](https://github.com/bitwes/Gut)
    - [GoDotTest by Chickensoft Games](https://github.com/chickensoft-games/GoDotTest)
    - [gdUnit4 by Mike Schulze](https://github.com/godot-gdunit-labs/gdUnit4)
- Games used as example:
    - [Michiball](https://nokorpo.com/projects/michiball): a local competitive party game where you win when you're the last animal standing
    - [GATO](https://nokorpo.com/projects/gato): a set of demos and tools to promote accessibility in Godot games
- [Godot benchmarks report](https://benchmarks.godotengine.org/)

### Contact

If you need help configuring this or kickstarting QA in your team, please contact us!

* Email: [{{site.data.social-media.email.id}}](mailto: {{site.data.social-media.email.id}})
* Mastodon: [{{site.data.social-media.mastodon.id}}]({{site.data.social-media.mastodon.href}})
* Bluesky: [{{site.data.social-media.bluesky.id}}]({{site.data.social-media.bluesky.href}})

