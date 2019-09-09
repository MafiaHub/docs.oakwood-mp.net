---
description: This page describes camera API methods
---

# Chat

## Set camera

`cameraSet(player,vec3,vec3)`

Lock camera to position

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |
| vec3 | Position |
| vec3 | Direction |

#### Returns
0 if successful, -1 if invalid

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Unlock camera

`cameraUnlock(player)`

Unlocks the camera to be returned back to player

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |

#### Returns
0 if successful, -1 if invalid

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Target player

`cameraTargetPlayer(player, player)`

Camera spectates player

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |
| player | Spectated Player |

#### Returns
0 if successful, -1 if invalid

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Target vehicle

`cameraTargetVehicle(vehicle, vehicle)`

Camera spectates vehicle

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |
| vehicle | Spectated Vehicle |

#### Returns
0 if successful, -1 if invalid

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}


## Target unset

`cameraTargetUnset(player)`

Camera will stop spectating entities

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |

#### Returns
0 if successful, -1 if invalid

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}
