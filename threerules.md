---
layout: page
title: "Three Rules LLC"
permalink: /threerules/
---

<script>
(function(){
    var asciiArtElement = document.getElementById('ascii-art');
    if (!asciiArtElement) {
        asciiArtElement = document.createElement('pre');
        asciiArtElement.id = 'ascii-art';
        asciiArtElement.style.textAlign = 'center'; // Center the ASCII art
        document.body.appendChild(asciiArtElement);
    }

    var width = 40;
    var height = 10;

    var positions = [
        { x: Math.floor(Math.random() * width), y: Math.floor(Math.random() * height), dx: 0.75, dy: 0.75 },
        { x: Math.floor(Math.random() * width), y: Math.floor(Math.random() * height), dx: -0.75, dy: 0.75 },
        { x: Math.floor(Math.random() * width), y: Math.floor(Math.random() * height), dx: 0.75, dy: -0.75 },
    ];

    function updatePositions() {
        positions.forEach(function(pos) {
            pos.x += pos.dx;
            pos.y += pos.dy;

            if (pos.x < 0) { pos.x = 0; pos.dx *= -1; }
            if (pos.x >= width) { pos.x = width - 1; pos.dx *= -1; }
            if (pos.y < 0) { pos.y = 0; pos.dy *= -1; }
            if (pos.y >= height) { pos.y = height - 1; pos.dy *= -1; }
        });
    }

    function drawFrame() {
        var frame = [];
        for (var y = 0; y < height; y++) {
            frame[y] = ' '.repeat(width).split('');
        }

        positions.forEach(function(pos, index) {
            frame[Math.round(pos.y)][Math.round(pos.x)] = 'O'; // Use 'O' for each ball
        });

        var frameText = frame.map(function(row) { return row.join(''); }).join('\n');

        asciiArtElement.textContent = frameText;
    }

    setInterval(function() {
        updatePositions();
        drawFrame();
    }, 125); // Increased interval slightly to slow down the animation
})();
</script>

## Contact

dtedesco1 at gmail dot com

Three Rules LLC 2024
