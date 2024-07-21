---
layout: page
title: "Now"
permalink: /now/
---

Last updated:  <span id="lastUpdated"></span>

## Where am I

Based in Beijing, China.

## What is my day job

I work for [Google](https://about.google/), now Data Lead for a 40-person team of international growth consultants across APAC. For my first five years at the company, I advised APAC game companies on international growth.

## What else am I spending time on

- Lots of exploratory coding with AIs like [Claude](https://claude.ai) and [Copilot](https://copilot.github.com/)
- Flora and I are getting ready for another visit to Japan for the Fuji Rock Festival
- Trying to get my Japanese to "intermediate" level and taking a live Japanese course with [Nihongodekita](https://nihongodekita.com/)
- Building an AI audio app with some friends on nights and weekends

## Games I'm playing

- Hearthstone
- Cities Skylines
- Zelda Tears of the Kingdom
- GTA V, again

<!-- Conway's Game of Life Footer Visualization -->
<canvas id="game"></canvas>
<script>
  // Create the lastUpdated variable
  var lastModified = new Date(document.lastModified);
  var options = { month: 'long', year: 'numeric' };
  document.getElementById('lastUpdated').textContent = lastModified.toLocaleDateString('en-US', options);
  // Get a reference to the canvas element
  const canvas = document.getElementById('game');
  const ctx = canvas.getContext('2d');
  canvas.width = window.innerWidth;
  canvas.height = 100;
  // canvas.style.position = "fixed"; // This will make it stick to the footer of the window
  canvas.style.position = "absolute"; // This will make it stick to the footer of the page
  canvas.style.bottom = "0";
  canvas.style.left = "0";
  // Update the width of the canvas whenever the window is resized
  window.onresize = function() {
    canvas.width = window.innerWidth;
  };
  // Define the dimensions of the grid
  const width = canvas.width;
  const height = canvas.height;
  const cellSize = 5;
  // Initialize the grid with random values
  let grid = new Array(height);
  for (let i = 0; i < height; i++) {
    grid[i] = new Array(width);
    for (let j = 0; j < width; j++) {
      grid[i][j] = Math.round(Math.random());
    }
  }
  // This function counts the number of alive neighbors of a given cell
  function countAliveNeighbors(grid, x, y) {
    let count = 0;
    for (let i = -1; i <= 1; i++) {
      for (let j = -1; j <= 1; j++) {
        if (i === 0 && j === 0) continue;
        if (x + i >= 0 && x + i < height && y + j >= 0 && y + j < width) {
          count += grid[x + i][y + j];
        }
      }
    }
    return count;
  }
  // This function updates the grid according to the rules of the game
  function update(grid) {
    let newGrid = new Array(height);
    for (let i = 0; i < height; i++) {
      newGrid[i] = new Array(width);
    }
    for (let i = 0; i < height; i++) {
      for (let j = 0; j < width; j++) {
        let aliveNeighbors = countAliveNeighbors(grid, i, j);
        if (grid[i][j] === 0 && aliveNeighbors === 3) {
          // Any dead cell with exactly 3 live neighbors becomes a live cell
          newGrid[i][j] = 1;
        } else if (grid[i][j] === 1 && (aliveNeighbors < 2 || aliveNeighbors > 3)) {
          // Any live cell with fewer than two live neighbors dies (underpopulation)
          // Any live cell with more than three live neighbors dies (overcrowding)
          newGrid[i][j] = 0;
        } else {
          // All other cells remain the same
          newGrid[i][j] = grid[i][j];
        }
      }
    }
    return newGrid;
  }
  // This function draws the grid and the cells on the canvas
  function draw(grid) {
    // Clear the canvas
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    // Draw the cells
    for (let i = 0; i < height; i++) {
        for (let j = 0; j < width; j++) {
            if (grid[i][j] === 1) {
                ctx.fillStyle
                // Set the fill color to black
                ctx.fillStyle = '#E5E4E2';
                // Calculate the coordinates of the cell
                let x = j * cellSize;
                let y = i * cellSize;
                // Draw a filled rectangle at the calculated coordinates
                ctx.fillRect(x, y, cellSize, cellSize);
            }
        }
    }
  }
  // This function animates the game by calling the draw function at a regular interval
  function animate() {
      // Update the grid
      grid = update(grid);
      // Draw the grid
      draw(grid);
      // Wait 100 milliseconds before printing the grid
      setTimeout(function() {
          // Request the next animation frame
          requestAnimationFrame(animate);
      }, 500);
  }
  // Start the animation
  requestAnimationFrame(animate);
</script>
