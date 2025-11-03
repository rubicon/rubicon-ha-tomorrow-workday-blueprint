# Rubicon HA: Tomorrow Workday Blueprint

This blueprint for [Home Assistant](https://www.home-assistant.io/) checks if tomorrow is a workday or school day and updates input boolean(s) accordingly.

**Two versions available:**
- **Standard Version** (`rubicon-ha-tomorrow-workday-blueprint.yaml`): Simple, single output boolean
- **Enhanced Version** (`rubicon-ha-tomorrow-workday-blueprint-enhanced.yaml`): Separate outputs + real-time state triggers

## Features

### Standard Version
- Supports multiple workday and school day binary sensors
- Combines all sensors into a single output boolean
- Time-based trigger only
- Simple and straightforward setup

### Enhanced Version
- **Separate outputs** for work night and school night status
- **Real-time state triggers** - updates immediately when sensor states change
- Single workday and single school day sensor
- Based on proven automation patterns
- More responsive to configuration changes

## Which Version Should I Use?

### Choose **Standard Version** if:
- You want to combine multiple work/school sensors into one output
- You only need daily checks at a specific time
- You prefer simpler configuration

### Choose **Enhanced Version** if:
- You want separate outputs for work night and school night
- You need real-time updates when sensor states change during the day
- You want behavior matching the proven "Update School/Work Night" automation pattern

## Installation

### One-click Installation (Standard Version)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Frubicon%2Frubicon-ha-tomorrow-workday-blueprint%2Fblob%2Fmain%2Frubicon-ha-tomorrow-workday-blueprint.yaml)

### One-click Installation (Enhanced Version)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Frubicon%2Frubicon-ha-tomorrow-workday-blueprint%2Fblob%2Fmain%2Frubicon-ha-tomorrow-workday-blueprint-enhanced.yaml)

### Manual Installation

1. Copy your chosen blueprint file into your Home Assistant `blueprints/automation/` directory:
   - Standard: `rubicon-ha-tomorrow-workday-blueprint.yaml`
   - Enhanced: `rubicon-ha-tomorrow-workday-blueprint-enhanced.yaml`
2. Reload automations in Home Assistant.

## Configuration

### Standard Version

When setting up an automation with this blueprint, you will configure:

- **Workday Binary Sensors**: One or more binary sensors for workday status
- **School Day Binary Sensors**: One or more binary sensors for school day status
- **Output Input Boolean**: A single input boolean to indicate tomorrow's status (on = workday/schoolday, off = neither)
- **Trigger Time**: Time for the automation to run (default: `00:01:00`)

**Example:**

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

### Enhanced Version

When setting up an automation with this blueprint, you will configure:

- **Workday Binary Sensor**: The binary sensor for workday status
- **School Day Binary Sensor**: The binary sensor for school day status
- **Work Night Input Boolean**: Input boolean for work night status
- **School Night Input Boolean**: Input boolean for school night status
- **Trigger Time**: Time for the automation to run (default: `00:00:00`)
- **Enable Real-Time State Triggers**: Toggle for real-time updates (default: enabled)

**Example:**

```yaml
blueprint:
  path: rubicon-ha-tomorrow-workday-blueprint/rubicon-ha-tomorrow-workday-blueprint-enhanced.yaml
  input:
    workday_sensor: binary_sensor.work_day
    schoolday_sensor: binary_sensor.school_day
    work_night_boolean: input_boolean.work_night
    school_night_boolean: input_boolean.school_night
    trigger_time: "00:00:00"
    enable_state_triggers: true
```

## Dependencies

Both blueprints require the following:

- **Home Assistant** version 2023.7.0 or higher (for `response_variable` support)
- **Home Assistant Workday Integration**: Provides binary sensors for workday status. See [Workday Integration](https://www.home-assistant.io/integrations/workday/) for setup details.
- **Home Assistant Binary Sensors**: For workday and school day status.
- **Input Boolean(s)**: Configurable entities for toggling tomorrow's workday status.

## Recent Improvements (2025)

### Standard Version
✅ **Fixed critical service call bug** - Now correctly calls `workday.check_date` for each sensor individually
✅ **Fixed response data handling** - Proper template logic for aggregating results
✅ **Added `min_version`** - Ensures compatibility (requires HA 2023.7.0+)
✅ **Updated `source_url`** - Correct repository reference
✅ **Improved documentation** - Better input descriptions and examples

### Enhanced Version (New!)
✨ **Created based on proven automation pattern**
✨ **Separate outputs** - Individual booleans for work night and school night
✨ **Real-time updates** - State triggers ensure immediate updates when sensors change
✨ **Correct service call implementation** - Properly uses `workday.check_date` response data
✨ **Follows HA best practices** - Modern blueprint schema with proper metadata

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
