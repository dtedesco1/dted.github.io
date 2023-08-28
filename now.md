---
layout: page
title: "Now"
permalink: /now/
---

## Where am I
Based in Beijing, China. Still reeling from spending a month in Tokyo, where Flora and I saw the [Foo Fighters](https://www.youtube.com/watch?v=l72CuN__pNo&t=3842s), [Blur](https://www.youtube.com/watch?v=JjQo7dbnMpk), [Cimafunk](https://youtu.be/AablKuz9UT4), [Liam Gallagher](https://youtu.be/Mwc7zPuqBTA).

## What is my day job
I work for [Google](https://about.google/), now Data Lead for a 40-person team of international growth consultants across APAC. For my first five years at the company, I advised APAC game companies on international growth.

## What else am I spending time on
- Launched a short course about Generative AI on [Datacamp](https://www.datacamp.com/).
- Flora and I recently moved into our new apartment in Beijing.
- Obessing over Open AI’s API and building little [web projects](/web.md) with it.
- Exploring blockchain and AI ecosystems, I [livestream](https://docs.google.com/document/d/1ta_6tSCGfC31iIfhz4bfC_oBKyNZGEdDsZkD-BRXY_Y/edit#heading=h.c65p4fi688tj) about it weekly 
- Interviewing folks on [The Craft Podcast](https://www.youtube.com/@thecraftpodcast).
- Lots of exercise via [Les Mills On Demand](https://www.lesmills.com/ondemand/).

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
