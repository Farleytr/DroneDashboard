# NOx meting Antwerpen

```js
import { FileAttachment } from "npm:@observablehq/stdlib";
import * as L from "npm:leaflet";
```

```js
//Load data

const nox = FileAttachment("nox-values.csv").csv({ typed: true });
const penguins = FileAttachment("penguins.csv").csv({ typed: true });
```

## Kaart

```js
display(nox[1].NOx);
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

## Waarden:

<div class="grid grid-cols-1">
 <div class="card">${Inputs.table(nox)}</div>
</div>
