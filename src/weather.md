---
theme: dashboard
toc: false
---

# Weather Report

```js
const forecast = FileAttachment('./data/forecast.json').json();
```

```js
function temperaturePlot(data, { width } = {}) {
	return Plot.plot({
		title: 'Hourly Temperature Forecast',
		width,
		x: { type: 'utc', ticks: 'day', label: null },
		y: { grid: true, inset: 10, label: 'Degrees (F)' },
		marks: [
			Plot.lineY(forecast.properties.periods, {
				x: 'startTime',
				y: 'temperature',
				z: null,
				stroke: 'temperature',
				curve: 'step-after'
			})
		]
	});
}
```

<div class="grid grid-cols-1">
  <div class="card">${resize((width) => temperaturePlot(forecast, {width}))}</div>
</div>
