---
layout: page
title: "Now"
permalink: /now/
---

## Where am I
Based in Beijing, China. Freshly returned from a trip to Thailand with Flora in mid-March.

## What is my day job
I work for [Google](https://about.google/), advising APAC game companies on international growth. I am also serving as Head of DAOs for [OpenESG](https://esgdao.earth/).

## What else am I spending significant time on
- Flora and I are getting ready to move into our new apartment in Beijing!
- Slowly learning guitar via the fantastic and free [JustinGuitar](https://www.justinguitar.com) site and Japanrse via Duolingo.
- Exploring blockchain and AI ecosystems, I [livestream](https://docs.google.com/document/d/1ta_6tSCGfC31iIfhz4bfC_oBKyNZGEdDsZkD-BRXY_Y/edit#heading=h.c65p4fi688tj) about it weekly and [interview folks](https://www.youtube.com/@thecraftpodcast).
- Lots of exercise via [Les Mills On Demand](https://www.lesmills.com/ondemand/).
- Reading Bee Democracy and Atomic Habits.

<!-- Conway's Game of Life Footer Visualization -->
<canvas id="game"></canvas>
<script>
  // Get a reference to the canvas element
  const canvas = document.getElementById('game');
  const ctx = canvas.getContext('2d');
  canvas.width = window.innerWidth;
  canvas.height = 100;
  canvas.style.position = "fixed";
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
