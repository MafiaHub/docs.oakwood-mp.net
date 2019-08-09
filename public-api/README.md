---
description: This page provides the list of Oakwood public API methods and events.
---

# Public API

{% hint style="danger" %}
**This section is under construction!**
{% endhint %}

## How does it work?

Our server exposes its public API via network protocols. We use 2 separate connections to handle 2 ways of communication:

* **Pub/Sub**: This is how we propagate changes to our scripts, as we call our server-defined events.
* **Req/Res**: Used by scripts to execute remote methods on the server-side expecting a result.

### Technology stack

We use `nanomsg` as our message broker, which gives us the ability to use various protocols \(TCP, IPC, ...\) and connection types.

To exchange data, we use `msgpack` for binary serialization. 

### Resources

Term _resources_ is loosely defined for scripts that implement logic for the server. These scripts could be game modes, small scripts such as announcements or an online map.

Resources can be written in any language that supports the technology stack we use, since they are standalone network clients connected to the server.

Check out [NodeJS](../languages/resource-nodejs.md) for an example of such language/ecosystem.

If you're interested in writing another language's integration, check out the [our tutorial](../tutorials/developer-api/).



