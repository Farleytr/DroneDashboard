# Weather report

```js
const forecast = FileAttachment("./data/forecast.json").json();
```

```js
function tempPlot(data, { width } = {}) {
  return Plot.plot({
    title: "Hourly temperature forecast",
    width,
    x: { type: "utc", ticks: "day", label: null },
    y: { grid: true, inset: 10, label: "Degrees (F)" },
    marks: [
      Plot.lineY(data.properties.periods, {
        x: "startTime",
        y: "temperature",
        z: null, // varying color, not series
        stroke: "temperature",
        curve: "step-after",
      }),
    ],
  });
}
```

<div class="grid grid-cols-1">
  <div class="card">${resize((width) => tempPlot(forecast, {width}))}</div>
</div>
<div class="grid grid-cols-2">
  <div class="card grid-colspan-2">one–two</div>
  <div class="card">three</div>
  <div class="card">four</div>
</div>
