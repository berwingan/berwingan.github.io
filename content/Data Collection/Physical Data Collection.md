---
title: Physical Data Collection
draft: false
---


test test1123123

## The base data
```dataview
TABLE sleep, activity
FROM "Daily Notes/2024" 

GROUP BY dateformat(file.day, "yyyy-'W'WW") as week 

FLATTEN sum(nonnull(rows.sleep))/length(nonnull(rows.sleep)) as sleep
FLATTEN sum(nonnull(rows.activity))/length(nonnull(rows.activity)) as activity 
```

## The bar chart
```dataviewjs
const result = await dv.tryQuery(`
  TABLE activity, sleep 
  FROM "Daily Notes/2024" 
  GROUP BY dateformat(file.day, "yyyy-'W'WW") as week 

  FLATTEN sum(nonnull(rows.sleep))/length(nonnull(rows.sleep)) as sleep
  FLATTEN sum(nonnull(rows.activity))/length(nonnull(rows.activity)) as activity 
`)

const myHeaders = result.headers
const myLabels = result.values.map(d => d[0])
const myData = result.values[0].map((_, colIndex) => result.values.map(row => row[colIndex]))

const chartData = {
  type: 'bar',
  data: {
    labels: myLabels,
    datasets: [{
      label: myHeaders[1],
      data: myData[1],
      backgroundColor: 'rgba(255, 99, 132, 0.2)',
      borderColor: 'rgba(255, 99, 132, 0.9)',
      borderWidth: 1,
      yAxisID: 'left-y-axis'
    }, {
      label: myHeaders[2],
      data: myData[2],
      backgroundColor: 'rgba(99, 255, 132, 0.2)',
      borderColor: 'rgba(99, 255, 132, 0.9)',
      borderWidth: 1,
      yAxisID: 'right-y-axis'
    },
    ]
  },
  options: {
    plugins: {
      legend: {
        position: 'bottom'
      }
    },
    scales: {
      'left-y-axis': {
        title: {
          display: true,
          text: "Percentage"
        },
        type: 'linear',
        position: 'left'
      },
      'right-y-axis': {
        title: {
          display: true,
          text: "Hours"
        },
        type: 'linear',
        position: 'right'
      }
    }
  }
}

window.renderChart(chartData, this.container)
```
