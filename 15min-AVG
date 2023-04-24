console.log("Test");
// Get the chart object
var chart = Highcharts.charts.slice(-1)[0];
// Extract the series data
var seriesData = chart.series[0].data;

// Calculate the average of y every 15 minutes
var newData = [];
var interval = 15 * 60 * 1000; // 15 minutes in milliseconds
var lastIntervalStart = Math.floor(seriesData[0].x / interval) * interval;
var sum = 0;
var count = 0;
for (var i = 0; i < seriesData.length; i++) {
    var point = seriesData[i];
    var intervalStart = Math.floor(point.x / interval) * interval;
    if (intervalStart != lastIntervalStart) {
        newData.push({
            x: lastIntervalStart + interval / 2,
            y: sum / count
        });
        sum = 0;
        count = 0;
        lastIntervalStart = intervalStart;
    }
    sum += point.y;
    count++;
}
newData.push({
    x: lastIntervalStart + interval / 2,
    y: sum / count
});

// Add the new series to the chart
chart.addSeries({
    name: '15-Minute Average',
    data: newData
});
