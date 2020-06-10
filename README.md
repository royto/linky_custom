# Linky Custom

[![GitHub release (latest by date)](https://img.shields.io/github/v/release/royto/linky_custom)](https://github.com/royto/linky_custom/releases)
![GitHub Release Date](https://img.shields.io/github/release-date/royto/linky_custom)
[![GitHub](https://img.shields.io/github/license/royto/linky_custom)](LICENSE)

[![GitHub issues](https://img.shields.io/github/issues/royto/linky_custom)](https://github.com/royto/linky_custom/issues)

The 'linky_custom' component is a Home Assistant custom sensors which calculate the cost of your daily consumption based on data provided by Enedis.

This component is inspired by [the work](https://github.com/home-assistant/core/pull/20535) of @Grea04.

You can use my [custom card](https://github.com/royto/linky-card) to display linky information

## Installation

### MANUAL INSTALLATION

1. Download the `linky_custom.zip` file from the
   [latest release](https://github.com/royto/linky_custom/releases/latest).
2. Unpack the release and copy the `custom_components/linky_custom` directory
   into the `custom_components` directory of your Home Assistant
   installation.
3. Configure the `linky_custom` sensor.
4. Restart Home Assistant.

### INSTALLATION VIA HACS

This repository is not included by default in HACS yet.

1. Ensure that [HACS](https://custom-components.github.io/hacs/) is installed.
1. Add this repository in custom repository as `integration`
1. Search for and install the "linky_custom" integration.
1. Configure the `linky_custom` sensor.
1. Restart Home Assistant.

## Configuration

### configuration.yaml

Add `linky_custom` sensor in your `configuration.yaml`.

```yaml
# Example configuration.yaml entry

sensor:
  - platform: linky_custom
    username: !secret linky_username
    password: !secret linky_password
    peak_hours:
      - ["03:00","15:30"]
      - ["17:30", "21:00"]
    peak_hours_cost: 0.1710
    offpeak_hours_cost: 0.1320
```

### CONFIGURATION PARAMETERS

|Parameter             |Optional|Description
|:---------------------|--------|------------
| `username`           | No  | Enedis account username
| `password`           | No  | Enedis account password
| `peak_hours`         | No  | Array of peak hours
| `peak_hours_cost`    | No  | kWh cost for peak hours
| `offpeak_hours_cost` | No  | kWh cost for off peak hours

## Linky Sensor

### State and Attributes

#### State

* The yesterday consumption in kWh.

### Attributes

* `daily` : array of daily consumption.
* `halfhourly` : array of yesterday consumption per 30 min.
* `peak_hours`: yesterday consumption in peak hours
* `offpeak_hours`: yesterday consumption in off peak hours
* `peak_offpeak_percent`: percentage of yesterday consumption in off peak
* `daily_cost`: yesterday cost
* `monthly_evolution`: percentage of consumption compare to same month of previous year

## Current Month Sensor

### State and Attributes

#### State

* The current month consumption in kWh.

### Attributes

* `time`: The month and year in format `mmm YYYY`.
* `username`: the Enedis account used.

## Last Month Sensor

### State and Attributes

#### State

* The last month consumption in kWh.

### Attributes

* `time`: The month and year in format `mmm YYYY`.
* `username`: the Enedis account used.

## Current Year Sensor

### State and Attributes

#### State

* The current year consumption in kWh.

### Attributes

* `time`: The year in format `YYYY`.
* `username`: the Enedis account used.

## Last Year Sensor

### State and Attributes

#### State

* The last year consumption in kWh.

### Attributes

* `time`: The year in format `YYYY`.
* `username`: the Enedis account used.
