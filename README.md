# Rubicon HA: Tomorrow Workday Blueprint

This blueprint for [Home Assistant](https://www.home-assistant.io/) checks if tomorrow is a workday or school day and updates a specified input boolean accordingly.

## Features

- Supports multiple workday and school day binary sensors.
- Dynamically calculates whether tomorrow is a workday or school day.
- Updates a specified input boolean to reflect the result.
- Configurable trigger time.
- Easy setup via Home Assistant's UI.

## Installation

### One-click Installation

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Frubicon%2Frubicon-ha-tomorrow-workday-blueprint%2Frubicon-ha-tomorrow-workday-blueprint.yaml)

### Manual Installation

1. Copy the `rubicon-ha-tomorrow-workday-blueprint.yaml` file into your Home Assistant `blueprints/automation/` directory.
2. Reload automations in Home Assistant.

## Configuration

When setting up an automation with this blueprint, you will configure:

- **Workday Binary Sensors**: One or more binary sensors for workday status.
- **School Day Binary Sensors**: One or more binary sensors for school day status.
- **Output Input Boolean**: An input boolean to indicate tomorrow’s status.
- **Trigger Time**: Time for the automation to run (default: `00:01:00`).

### Example

```yaml
blueprint:
  path: rubicon-ha-tomorrow-workday-blueprint/rubicon-ha-tomorrow-workday-blueprint.yaml
  input:
    workday_sensors:
      - binary_sensor.work_day
    schoolday_sensors:
      - binary_sensor.school_day
    output_boolean: input_boolean.tomorrow_is_a_workday
    trigger_time: "00:01:00"
```

## Dependencies

This blueprint requires the following:

- **Home Assistant Workday Integration**: Provides binary sensors for workday status. See [Workday Integration](https://www.home-assistant.io/integrations/workday/) for setup details.
- **Home Assistant Binary Sensors**: For workday and school day status.
- **Input Boolean**: A configurable entity for toggling tomorrow’s workday status.

## Support

Please [create an issue](https://github.com/rubicon/rubicon-ha-tomorrow-workday-blueprint/issues) in this repository for questions, feature requests, or issues.

## License

This project is licensed under the MIT License.

### License and Copyright Notice

MIT License

Copyright (c) 2024 Rubicon

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
