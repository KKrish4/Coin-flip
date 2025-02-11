# Coin-flip
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Coin Flip</title>
    <style>
        body {
            margin: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: Arial, sans-serif;
            font-size: 2rem;
            background-color: #f4f4f4;
            user-select: none;
            text-align: center;
        }
        #coin {
            position: absolute;
        }
    </style>
</head>
<body>
    <div id="coin">Tap to Flip</div>
    <script>
        document.body.addEventListener("click", function(event) {
            let screenHeight = window.innerHeight;
            let coin = document.getElementById("coin");
            
            if (event.clientY < screenHeight / 2) {
                coin.textContent = "Tails";
            } else {
                coin.textContent = "Heads";
            }
        });
    </script>
</body>
</html>
