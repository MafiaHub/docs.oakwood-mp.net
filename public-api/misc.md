---
description: This page describes miscellaneous API methods
---

# Miscellaneous

## Killbox set

`killboxSet(float)`

Sets the height level under which we kill or despawn an entity.

{% tabs %}
{% tab title="Details" %}
#### Remarks

The default value is `-40`. This can also be set from the server config.

#### Arguments

| Type | Description |
| :--- | :--- |
| float | Y level height |

#### Returns

0 if successful, -1 if invalid

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Killbox get

`killboxGet()`

Retrieves the current height level at which we kill/despawn an entity.

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

None.

#### Returns

The current height level.

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

