# Examples - Performing Actions

## Using Tap Actions

The `flex-table-card` supports the same tap actions as many other Home Assistant cards, namely `tap_action`, 
`hold_action`, and `double_tap_action`. In addition, it supports the `edit_action` which will be covered below.

The use of Actions in Home Assistant is described [here](https://www.home-assistant.io/dashboards/actions/). The behavior
of the `flex-table-card` is similar to that of the cards mentioned in the list.

When a column has been configured for actions, the cells of that column will change color when a mouse hovers over them.

Note that the default size of cells may be too small to be accurately controlled with finger touches. You can use CSS
to increase the size of cells, as shown in some of the examples below.

### Calling the `more-info` Action using `tap_action`

To perform the `more-info` Action when a cell in a configured column in `flex-table-card` is tapped, 
you can use a card definition like below. Here, when a row in the Temperature column is tapped, a More Info popup will be displayed.

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

You can use a definition like the following to perform any supported Home Assistant action. This example demonstrates the
use of `hold_action`. When you press and hold your mouse or finger on a cell for more than half a second, 
you will see a visual cue when the action is ready to activate. Release to fire the action. 
Move your mouse or finger off the cell before releasing to cancel the action.

This example also demonstrates the use of `confirmation` to confirm the action. The `confirmation` option may be used on any action type.

```yaml

```



[Return to main README.md](../README.md)
