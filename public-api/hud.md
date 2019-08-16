---
description: This page describes the HUD API
---

# HUD

## Fadeout

`hudFadeout(player, int, int, int)`

Fades the screen to a specified color with a duration.

{% tabs %}
{% tab title="Details" %}
#### Remarks

Has to be called twice to cause blink effect, see example.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |
| int | 0 for fadeout, 1 to fade in |
| int | Transition duration |
| int | Color to fade into / fade out from |

#### Returns

0 if successful, -1 if failed
{% endtab %}

{% tab title="Example" %}
```javascript
oak.event('playerConnect', async pid => {
    console.log('[info] player connected', pid)

    // Cause a white blink effect
    oak.hudFadeout(pid, 1, 0.5, 0xFFFFFF)
    oak.hudFadeout(pid, 0, 0.5, 0xFFFFFF)

    oak.playerPositionSet(pid, [-1774.59301758, -4.88487052917, -2.40491962433])
    oak.playerHealthSet(pid, 200)
    oak.playerSpawn(pid)
})
```
{% endtab %}
{% endtabs %}

## Countdown

`hudCountdown(player, int)`

Displays a race countdown number.

{% tabs %}
{% tab title="Details" %}
#### Remarks

Call it in interval to actually count numbers down.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |
| int | Race countdown stage |
| int | Transition duration |
| int | Color to fade into / fade out from |

#### Returns

0 if successful, -1 if failed

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Alert

`hudAlert(player, string)`

Displays a splash/alert message in the centre of the screen.

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |
| string | Text to display |

#### Returns

0 if successful, -1 if failed

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}
