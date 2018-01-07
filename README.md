# A custom state card for scripts/scenes in [Home Assistant](https://home-assistant.io)

It is highly inspired from [Home Assistant Tiles](https://github.com/c727/home-assistant-tiles)

This custom ui is designed to summarize [script](https://home-assistant.io/components/script/) (which can be also a scene) in a single entity on a group state card and show the active script/scene by a [binary mqtt sensor](https://home-assistant.io/components/binary_sensor.mqtt/).
Usually you set the [binary mqtt sensor](https://home-assistant.io/components/binary_sensor.mqtt/). by a [script](https://home-assistant.io/components/script/), that the custom ui is able to show the current state. 

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
        - entity: script.scene_movie # the script/scene you want to call
          friendly_name: Movie #define icon and friendly_name or both
          icon: mdi:movie #define icon and friendly_name or both
          state: binary_sensor.scene_movie_state # the binary sensor to determine the current state
        - entity: script.scene_romance
          friendly_name: Romance
          icon: mdi:heart
          state: binary_sensor.scene_romance_state
        - entity: script.scene_chill
          friendly_name: Chill
          icon: mdi:sunglasses
          state: binary_sensor.scene_chill_state
 ```
