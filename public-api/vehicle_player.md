---
description: This page describes the player-vehicle interaction API
---

# Player-Vehicle interaction

## Player put

`vehiclePlayerPut(vehicle, player, seat_id)`

Puts player into a vehicle at a specified seat.

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |
| player  | Player ID |
| seat_id | Seat slot |

#### Returns

0 if successful, -1 if occupied already

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Player remove

`vehiclePlayerRemove(vehicle, player)`

Removes player from a vehicle.

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |
| player  | Player ID |

#### Returns

0 if successful, -1 if not in a vehicle.

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Player inside

`vehiclePlayerInside(player)`

Get the current vehicle player sits in.

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| player  | Player ID |

#### Returns

Vehicle ID or -1 if not inside a vehicle.

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Player seat get

`vehiclePlayerSeatGet(vehicle, player)`

Retrieves the seat slot of a player in specified vehicle

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |
| player  | Player ID |

#### Returns

Seat ID of a player or -1 if not inside specified vehicle.

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Player at seat

`vehiclePlayerAtSeat(vehicle, seat_id)`

Retrieves a player ID at a specified seat slot of a specified vehicle.

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |
| seat_id  | Seat slot |

#### Returns

Player ID at a specified seat or -1 if seat is empty.

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}
