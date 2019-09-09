---
description: This page describes the vehicle API
---

# Vehicle

## Spawn

`vehicleSpawn(string, vec3, float)`

Spawns the vehicle at a specified position and heading direction.

{% tabs %}
{% tab title="Details" %}
#### Remarks

You can use the following [listing](../assets/asset-vehicle-models.md) for vehicle model names.

#### Arguments

| Type | Description |
| :--- | :--- |
| string | Model name |
| vec3 | Position |
| float | Heading direction |

#### Returns

Vehicle ID if spawned, -1 if failed.

{% endtab %}

{% tab title="Example" %}
```javascript
oak.cmd('car', async (pid, model) {
    const m = parseInt(model)

    if (m === NaN) {
        return oak.chatSend(pid, "[error] provided argument should be a valid number")
    }

    oak.chatSend(pid, "[info] spawning vehicle model ${vehicleModels[m][0]}")

    let pos = await oak.playerPositionGet(pid)
    let heading = await oak.playerHeadingGet(pid)

    if (adjustPos === true) {
        let dir = await oak.playerDirectionGet(pid)
        pos = pos.map((p, i) => p + dir[i] * 1.5)
        heading -= 90.0
    }

    oak.vehicleSpawn(vehicleModels[m][1], pos, heading)
})
```
{% endtab %}
{% endtabs %}

## Despawn

`vehicleDespawn(vehicle)`

Despawns a vehicle

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |

#### Returns

0 if successful, -1 if failed.

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Invalid

`vehicleInvalid(vehicle)`

Checkes whether the vehicle ID is invalid.

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |

#### Returns

1 if invalid, 0 if valid otherwise.

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Repair

`vehicleRepair(vehicle)`

Repairs the vehicle.

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |

#### Returns

0 if successful, -1 if failed.

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Set position

`vehiclePositionSet(vehicle, vec3)`

Sets the vehicle position.

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |
| vec3 | Vehicle Position |

#### Returns

0 if successful, -1 if failed.

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Set direction

`vehicleDirectionSet(vehicle, vec3)`

Sets the vehicle forward direction vector.

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |
| vec3 | Vehicle Direction |

#### Returns

0 if successful, -1 if failed.

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Set heading

`vehicleHeadingSet(vehicle, float)`

Sets the vehicle heading angle.

{% tabs %}
{% tab title="Details" %}
#### Remarks

Uses a ±180 degree format.

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |
| float | ±180 degree angle |

#### Returns

0 if successful, -1 if failed
{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Set fuel

`vehicleFuelSet(vehicle, float)`

Set vehicle fuel level

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |
| float | Fuel level |

#### Returns

0 if successful, -1 if failed
{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Set transparency

`vehicleTransparencySet(vehicle, float)`

Set vehicle transparency value

{% tabs %}
{% tab title="Details" %}
#### Remarks

0-1 range.

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |
| float | transparency value |

#### Returns

0 if successful, -1 if failed
{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Get position

`vehiclePositionGet(vehicle)`

Gets the vehicle position.

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |

#### Returns

Returns vehicle position

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}


## Get direction

`vehicleDirectionGet(vehicle)`

Gets the vehicle direction.

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |

#### Returns

Returns vehicle direction

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Get heading

`vehicleHeadingGet(vehicle)`

Retrieves the vehicle's heading angle.

{% tabs %}
{% tab title="Details" %}
#### Remarks

Uses a ±180 degree format.

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |

#### Returns

`float` heading angle
{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Get fuel

`vehicleFuelGet(vehicle)`

Retrieves the vehicle's fuel level.

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |

#### Returns

`float` fuel level
{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Get transparency

`vehicleTransparencyGet(vehicle)`

Retrieves the vehicle's transparency value.

{% tabs %}
{% tab title="Details" %}
#### Remarks

0-1 range.

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |

#### Returns

`float` transparency value
{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Visibility

There are several visibility options you can set for the vehicle:

| Name | Description |
| :--- | :--- |
| VISIBILITY\_ICON | Vehicle's blip visibility on the map |
| VISIBILITY\_RADAR | Vehicle's marker visibility on the radar |
| VISIBILITY\_COLLISION | Vehicle's collision state |
| VISIBILITY\_MODEL | Vehicle's transparency state |

### Get visibility

`vehicleVisibilityGet(vehicle, visibility_type)`

Retrieves the current vehicle's visibility.

{% tabs %}
{% tab title="Details" %}
#### Remarks

None.

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |
| visibility\_type | Visibility option |

#### Returns

`int` vehicle visibility option value

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

### Set visibility

`vehicleVisibilitySet(vehicle, visibility_type, int)`

Sets the current vehicle's visibility setting.

{% tabs %}
{% tab title="Details" %}
#### Remarks

None.

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |
| visibility\_type | Visibility option |
| int | Visibility state |

#### Returns

0 if successful
{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

