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
 ```

```yaml
binary_sensor:
- platform: mqtt
  state_topic: "hass/script/scenes/movie_state"
  name: script_scene_movie_state
  payload_on: "ON"
  payload_off: "OFF"
```

```yaml
script:
  scene_movie:
    sequence:
      - service: light.turn_on
        data:
          entity_id: light.ceilinglight
          transition: 1
          brightness: 80
          color_temp: 360
      - service: mqtt.publish
        data:
          topic: "hass/script/scenes/movie_state"
          payload: 'ON'
          retain: 'true'
```

configuration.yaml

```yaml

input_boolean:
   sensor1:
   sensor2:
   
homeassistant:
  customize:
    input_boolean.sensor1:
      icon: mdi:thermometer-lines
      friendly_name: sensor1
      custom_ui_state_card: state-card-custom_sensor
      config:
        entities: 
          -sensor.bedroom_temp
          -sensor.bedroom_humidity
 ```        
          
