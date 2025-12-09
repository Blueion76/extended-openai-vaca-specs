# extended-openai-vaca-specs
This repo houses my personal Extended OpenAI View Assist / HA Voice specs allowing an LLM to do things like set timers, alarms, reminders etc.


Make sure you have a Home Assistant automation like the following set up with a helper.

```
alias: Set Last Used Voice Satellite Device ID
description: Stores the device_id of the last used assist satellite
triggers:
  - entity_id:
      - assist_satellite.vaca_eb0bb2b96_2
      - (more satellites)
    to:
      - listening
    trigger: state
conditions: []
actions:
  - target:
      entity_id: input_text.last_used_satellite_device_id
    data:
      value: "{{ device_id(trigger.entity_id) }}"
    action: input_text.set_value
mode: single
```
