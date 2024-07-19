git clone https://github.com/tu-usuario/kaleidoscope-app.git
cd kaleidoscope-app
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Kaleidoscope</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div id="controls">
        <input type="file" id="imageLoader" name="imageLoader"/>
        <label for="slices">Number of Slices:</label>
        <input type="range" id="slices" name="slices" min="3" max="24" value="6">
    </div>
    <canvas id="kaleidoscopeCanvas"></canvas>
    <script src="script.js"></script>
</body>
</html>
