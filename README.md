<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Coin Flip with Image</title>
    <style>
        /* General Page Styles */
        body, html {
            height: 100%;
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            background-color: #f7f7f7;
            font-family: Arial, sans-serif;
            cursor: pointer; /* Set cursor to pointer for clicks */
            transition: background-color 0.3s ease-in-out; /* Smooth background transition */
        }

        /* Coin Container - Circular and Neutral */
        .coin-container {
            width: 200px;
            height: 200px;
            background-color: #f1c40f; /* Golden color to look like a coin */
            border-radius: 50%; /* Circular Shape */
            position: relative;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            cursor: pointer;
            display: flex;
            justify-content: center;
            align-items: center;
            text-align: center;
            font-size: 32px;
            font-weight: bold;
            color: #fff;
            text-transform: uppercase;
            transition: transform 0.8s ease; /* Smooth flip transition */
            overflow: hidden;
        }

        /* Coin Image - Logo or Image on Coin */
        .coin-image {
            position: absolute;
            width: 80px;  /* Adjust size of the image */
            height: 80px;
            background-image: url('https://via.placeholder.com/80'); /* Your image URL here */
            background-size: cover;
            background-position: center;
            border-radius: 50%; /* Make the image circular */
        }

        /* Result Text */
        .result {
            position: absolute;
            font-size: 32px;
            font-weight: bold;
            color: #333;
            text-transform: uppercase;
            opacity: 0; /* Initially hidden */
        }

        /* Animation for Result */
        @keyframes flipAnimation {
            0% {
                transform: rotateY(0deg);
                opacity: 0;
            }
            50% {
                transform: rotateY(180deg);
                opacity: 0.5;
            }
            100% {
                transform: rotateY(360deg);
                opacity: 1;
            }
        }

        .show-result {
            animation: flipAnimation 1s ease-out forwards;
        }

        /* Hand Flip Effect */
        .flip {
            transform: rotateY(720deg);
        }
    </style>
</head>
<body>
    <div class="coin-container" onclick="flipCoin(event)">
        <div id="result" class="result"></div>
        <div class="coin-image"></div> <!-- The image on the coin -->

    </div>

    <script>
        function flipCoin(event) {
            const resultDiv = document.getElementById('result');
            const coin = document.querySelector('.coin-container');
            resultDiv.classList.remove('show-result'); // Reset animation
            resultDiv.style.opacity = 0; // Hide result initially

            // Get the X position of the click relative to the screen
            const clickX = event.clientX;
            const screenWidth = window.innerWidth;

            // Determine the outcome based on whether the click was on the left or right side
            let result = '';
            let bgColor = ''; // Variable to change background color

            if (clickX < screenWidth / 2) {
                result = 'Tails'; // Left side
                bgColor = '#3498db'; // Change background to blue for left click
            } else {
                result = 'Heads'; // Right side
                bgColor = '#2ecc71'; // Change background to green for right click
            }

            // Change the background color of the body based on the click side
            document.body.style.backgroundColor = bgColor;

            // Add flip animation
            coin.classList.add('flip');

            // Show the result with animation
            setTimeout(function() {
                resultDiv.innerText = result;
                resultDiv.style.opacity = 1;
                resultDiv.classList.add('show-result');
            }, 800); // Delay before showing result after flip is completed (800ms)

            // Remove the flip effect after animation ends (so it can be reused next time)
            setTimeout(function() {
                coin.classList.remove('flip');
            }, 1000); // Animation duration (same as flip duration)
        }
    </script>
</body>
</html>
