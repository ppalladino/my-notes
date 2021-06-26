---
description: A list of things to to when setting up my local development environment
---

# Local Dev Setup

## ~/.bash\_profile

Make local NODE\_ENV=development aid w/ debugging

```
$ echo export "NODE_ENV=development" >> ~/.bash_profile
```

{% hint style="danger" %}
Do not ship with this setting! Make sure production artifacts use NODE\_ENV=production
{% endhint %}



Once you're strong enough, save the world:

{% code title="hello.sh" %}
```bash
# Ain't no code for that yet, sorry
echo 'You got to trust me on this, I saved the world'
```
{% endcode %}



