---
toc: false
---

<style>

.hero {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: var(--sans-serif);
  margin: 4rem 0 8rem;
  text-wrap: balance;
  text-align: center;
}

.hero h1 {
  margin: 2rem 0;
  max-width: none;
  font-size: 14vw;
  font-weight: 900;
  line-height: 1;
  background: linear-gradient(30deg, var(--theme-foreground-focus), currentColor);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero h2 {
  margin: 0;
  max-width: 34em;
  font-size: 20px;
  font-style: initial;
  font-weight: 500;
  line-height: 1.5;
  color: var(--theme-foreground-muted);
}

@media (min-width: 640px) {
  .hero h1 {
    font-size: 90px;
  }
}

</style>
```js
import { FileAttachment } from "npm:@observablehq/stdlib";
import * as L from "npm:leaflet";
```
```js
//Load data
const nox = FileAttachment("./data/nox-values.csv").csv({ typed: true });
const penguins = FileAttachment("penguins.csv").csv({ typed: true });
```

<div class="hero">
  <h1>NOx meting</h1>
  <!-- <h2>Kaart</h2> -->
</div>

## Kaart:

```js 
//display(nox[1].NOx);
const div = display(document.createElement("div"));
div.style = "height: 500px;";

const map = L.map(div).setView([51.2732205232446, 4.354043935211869], 11);

L.tileLayer("https://tile.openstreetmap.org/{z}/{x}/{y}.png", {
  attribution:
    '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a>',
}).addTo(map);
for (let x = 0; x < nox.length; x++) {
  L.marker([nox[x].Lat, nox[x].Long]).addTo(map).bindPopup(String(nox[x].NOx));
  // .openPopup();
}
```
---

## Waarden:

<div class="grid grid-cols-1">
 <div class="card">${Inputs.table(nox)}</div>
</div>

---
