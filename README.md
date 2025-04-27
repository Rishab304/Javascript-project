<!DOCTYPE html>
<html lang="en">
<head>
    <title>Javascript Timer</title>
    <style>
        body {
            height: 100vh;
            background-color: blueviolet;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            margin: 0;
        }

        #box {
            width: 300px;
            height: auto;
            background-color: aquamarine;
            border-radius: 30px;
            text-align: center;
            padding: 20px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }

        h1 {
            margin: 0;
            color: #333;
        }

        #text {
            width: 100%;
            padding: 10px;
            border-radius: 10px;
            border: 1px solid #ccc;
            margin-bottom: 10px;
            font-size: 16px;
        }

        button {
            padding: 10px 20px;
            background-color: #ff6347;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #ff4500;
        }

        #h {
            margin: 10px 0;
            font-size: 24px;
            font-weight: bold;
            transition: all 0.3s ease;
        }
    </style>
</head>
<body>
    <h1>Your Timer</h1>
    <div id="box">
        <input id="text" type="number" placeholder="Enter seconds" min="1">
        <h1 id="h">Here we go again</h1>
        <button onclick="run()">Start</button>
        <button onclick="reset()">Reset</button>
    </div>

    <script>
        let interval;

        function run() {
            const textInput = document.getElementById("text");
            let num = parseInt(textInput.value);

            // Input validation
            if (isNaN(num) || num <= 0) {
                alert("Please enter a positive number!");
                return;
            }

            function count() {
                const h1Ele = document.getElementById("h");

                if (num > 0) {
                    h1Ele.innerHTML = num;
                    num--;
                    h1Ele.style.backgroundColor = "pink";
                    h1Ele.style.width = "80px";
                    h1Ele.style.height = "80px";
                    h1Ele.style.borderRadius = "50%";
                    h1Ele.style.textAlign = "center";
                    h1Ele.style.lineHeight = "80px";
                    h1Ele.style.margin = "10px auto";
                } else {
                    clearInterval(interval);
                    h1Ele.innerHTML = "Time's up!";
                    h1Ele.style.backgroundColor = "";
                    h1Ele.style.width = "";
                    h1Ele.style.height = "";
                    h1Ele.style.borderRadius = "";
                }
            }

            // Clear previous interval if any
            clearInterval(interval);
            interval = setInterval(count, 1000);
        }

        function reset() {
            clearInterval(interval);
            document.getElementById("h").innerHTML = "Here we go again";
            document.getElementById("text").value = "";
            const h1Ele = document.getElementById("h");
            h1Ele.style.backgroundColor = "";
            h1Ele.style.width = "";
            h1Ele.style.height = "";
            h1Ele.style.borderRadius = "";
        }
    </script>
</body>
</html># Javascript-project
