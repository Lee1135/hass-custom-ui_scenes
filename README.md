# A custom state card for scripts/scenes in [Home Assistant](https://home-assistant.io)

It is highly inspired from [Home Assistant Tiles]https://github.com/c727/home-assistant-tiles

## Installation
* Download `/www/custom_ui/state-card-custom_scenes.html` to `<config-dir>/www/custom_ui/state-card-custom_scenes.html`
* Add it to your `configuration.yaml`:
```yaml
frontend:
  extra_html_url:
    - /local/custom_ui/state-card-custom_scenes.html
```

## Configuration
```yaml
homeassistant:
  customize:
    group.scenes:
	  custom_ui_state_card: state-card-custom_scene
		config:
			entities:
			- entity: script.scene_movie
			friendly_name: Movie
			- entity: script.scene_romance
			friendly_name: Romance
			- entity: script.scene_chill
			friendly_name: Chill
 ```
