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
body {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: #f0f0f0;
}

#controls {
    margin-bottom: 10px;
}

#kaleidoscopeCanvas {
    border: 1px solid #000;
}
const canvas = document.getElementById('kaleidoscopeCanvas');
const ctx = canvas.getContext('2d');
const imageLoader = document.getElementById('imageLoader');
const slicesInput = document.getElementById('slices');
let image = new Image();

canvas.width = 800;
canvas.height = 800;

imageLoader.addEventListener('change', handleImage, false);
slicesInput.addEventListener('input', drawKaleidoscope, false);

function handleImage(e) {
    const reader = new FileReader();
    reader.onload = function(event) {
        image.onload = function() {
            drawKaleidoscope();
        }
        image.src = event.target.result;
    }
    reader.readAsDataURL(e.target.files[0]);
}

function drawKaleidoscope() {
    const slices = slicesInput.value;
    const sliceAngle = 360 / slices;
    const halfWidth = canvas.width / 2;
    const halfHeight = canvas.height / 2;

    ctx.clearRect(0, 0, canvas.width, canvas.height);

    for (let i = 0; i < slices; i++) {
        ctx.save();
        ctx.translate(halfWidth, halfHeight);
        ctx.rotate((i * sliceAngle * Math.PI) / 180);
        ctx.drawImage(image, -halfWidth, -halfHeight, canvas.width, canvas.height);
        ctx.restore();
    }
}
git add .
git commit -m "Initial commit"
git push origin main
