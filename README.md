In-Class-Substitution-Excercise
Escape room game using Midjourney, Google Gemini and P5.js


Code:
let backgroundImage;
let keyFound = false;
let gameEnded = false;
let message = '';

function preload() {
  // Load the background image before the setup starts
  backgroundImage = loadImage('escaperoom1.png'); // Make sure this is the correct path
}

function setup() {
  createCanvas(768, 768);
  noLoop(); // Since the background is static, no need to loop
}

function draw() {
  // If the game has not ended, show the background
  if (!gameEnded) {
    background(backgroundImage);
  } else {
    // If the game has ended, display the end screen
    endGame();
  }
}

function mousePressed() {
  if (gameEnded) return; // If the game has ended, do not respond to clicks

  // Check for clicks and update the message based on the clickable area
  if (!keyFound && mouseX >= 0 && mouseX <= 50 && mouseY >= 650 && mouseY <= 768) {
    keyFound = true;
    message = "You found a key! Find your way out!";
    displayMessage(message);
  } else if (mouseX >= 100 && mouseX <= 350 && mouseY >= 500 && mouseY <= 650) {
    message = "A messy bed, something might be hidden here.";
    displayMessage(message);
  } else if (mouseX >= 50 && mouseX <= 250 && mouseY >= 50 && mouseY <= 300) {
    message = "Bookshelves with various knick-knacks.";
    displayMessage(message);
  } else if (keyFound && mouseX >= 450 && mouseX <= 850 && mouseY >= 250 && mouseY <= 1000) {
     message = "You found the key!";
    displayMessage(message);
    gameEnded = true;
    redraw(); // Ensure that the endGame screen is drawn even though noLoop is set
  } else {
    message = ''; // Clear message when clicking on non-interactive areas
  }
}

// Function to display a message
function displayMessage(msg) {
  clear();
  background(backgroundImage);
  fill(0); // Black color for the text
  stroke(255); // White outline for readability
  strokeWeight(4); // Thickness of the text outline
  textSize(18); // Size of the text
  textAlign(CENTER, BOTTOM); // Align the text to the center and bottom
  text(msg, width / 2, height - 20);
}

// Function to display the end game screen
function endGame() {
  background(0); // Set background to black
  fill(255); // Set text color to white
  textSize(32); // Increase text size
  textAlign(CENTER, CENTER); // Center the text
  text("You escaped!", width / 2, height / 2);
}

// Disable right-click context menu
window.addEventListener('contextmenu', function (e) {
  e.preventDefault();
});


Image:
![escaperoom1](https://github.com/boatboyrob27/In-Class-Substitution-Excercise/assets/160073731/217fa3e4-aca3-4b76-9fd4-196bf1975e82)





Reflection:
To start things off I had a lot of fun doing this assignment as I was doubting myself going into it. I am not the best at writing code so struggled greatly on debugging the code. My first main issue I ran into was simply inputting my image into P5. I soon realized this was just user error and move on quickly with the image showing up in the window. The next problem I had was trying to use Chat GPT to write the script for the game. The code just did not do what I wanted so I moved onto Google Gemini. That is where things started to make sense and Gemini began learning what I wanted it to create. I did have to ask Gemini to alter the code numerous times when P5 alerted me about certain lines not working. Once the code worked and text was displaying on the screen when clicking in certain areas, I had to move around the coordinates to fit where the objects were on the screen. This took a lot of guessing but I finally got things to work on a “mis-click” where I clicked the wrong button and tried it for the heck of it and things worked. I was very pleased with the outcome of this game as this was the first time I had ever created anything of this caliber. 





