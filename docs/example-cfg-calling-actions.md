# Examples - Performing Actions

## Using Tap Actions

The `flex-table-card` supports the same tap actions as many other Home Assistant cards, namely the `tap_action`, 
`hold_action`, and the `double_tap_action`. In addition, it supports the `edit_action` which will be covered below.

The use of Actions in Home Assistant is described [here](https://www.home-assistant.io/dashboards/actions/).

### Calling the `more-info` Action using `tap_action`

To perform the `more-info` Action when a single column in a `flex-table-card` is tapped, you can use a card definition like below.
When a row in the Temperature column is tapped, a More Info popup will be displayed.

(Alternatively, you can set `clickable=true` on the entire card to perform the `more-info` Action on all columns of the card.)

``` yaml
type: custom:flex-table-card
entities:
  include:
    - sensor.*stairs*_temperature
auto_format: true
columns:
  - name: Name
    data: friendly_name
  - name: Temperature
    data: state
    tap_action:
      action: more-info
```

The resulting card and dialog are:

<img src="../images/TemperatureTapAction.png" alt="Display More Info using tap_action_" width="500px">

### Calling the `toggle` Action using `double_tap_action`

The following definition shows how to toggle an entity using the `double_tap_action`. 
When a row in the State column is double-tapped, the entity's state will be toggled.

```yaml
type: custom:flex-table-card
entities:
  include:
    - light.bed*
auto_format: true
columns:
  - name: Name
    data: friendly_name
  - name: State
    data: state
    double_tap_action:
      action: toggle
```

<img src="../images/DoubleTapExample.png" alt="Toggle lights using double_tap_action" width="500px">

### Calling the `perform-action` Action using `hold_action`

You can use a definition like the following to perform any Home Assistant action by holding your mouse or finger on a 
column for more than half a second. The cell will change color when ready to active. Move your mouse or finger off the
cell before releasing to cancel the action.

This example also demonstrates the use of `confirmation` to confirm the action. The `confirmation` option may be used on any action type.

```yaml

```



[Return to main README.md](../README.md)
