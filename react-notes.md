# React Notes

## Project Set-Up

### Strict Mode <a id="strict-mode"></a>

Strict mode is opinionated and will help us not do things that we should't do

Go to App.js and wrap `<App />` in the render call in `<StrictMode>`.

{% code title="App.js" %}
```bash

// import at top
import { StrictMode } from "react";

// replace render
render(
  <StrictMode>
    <App />
  </StrictMode>,
  document.getElementById("root")
);
```
{% endcode %}

{% hint style="info" %}
 Super-powers are granted randomly so please submit an issue if you're not happy with yours.
{% endhint %}

### Error Boundaries

{% hint style="warning" %}
Only works with Class componets 
{% endhint %}

{% code title="hello.sh" %}
```bash
# Ain't no code for that yet, sorry
echo 'You got to trust me on this, I saved the world'
```
{% endcode %}



