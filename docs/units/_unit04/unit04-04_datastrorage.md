<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Live Graph</title>
  <!-- Include Plotly.js library -->
  <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
</head>
<body>
  <!-- Container for the graph -->
  <div id="graph"></div>

  <script>
    // Function to update the graph
    function updateGraph(xValues, yValues, zValues) {
      // Define traces for y and z
      var traceY = {
        x: xValues,
        y: yValues,
        mode: 'lines',
        name: 'y'
      };

      var traceZ = {
        x: xValues,
        y: zValues,
        mode: 'lines',
        name: 'z'
      };

      // Plot the graph
      Plotly.newPlot('graph', [traceY, traceZ]);
    }

    // Example data
    var initialXValues = [1, 2, 3, 4, 5];
    var initialYValues = [10, 11, 12, 13, 14];
    var initialZValues = [20, 19, 18, 17, 16];

    // Initial plot
    updateGraph(initialXValues, initialYValues, initialZValues);

    // Example function to simulate updating the graph with new data
    function simulateUpdate() {
      var newXValues = initialXValues.map(function(value) {
        return value + Math.random(); // Randomly change x values
      });
      var newYValues = initialYValues.map(function(value) {
        return value + Math.random(); // Randomly change y values
      });
      var newZValues = initialZValues.map(function(value) {
        return value + Math.random(); // Randomly change z values
      });

      // Update the graph with new data
      updateGraph(newXValues, newYValues, newZValues);
    }

    // Simulate updating the graph every 2 seconds
    setInterval(simulateUpdate, 2000);
  </script>
</body>
</html>
