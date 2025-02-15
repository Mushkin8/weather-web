# weather 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Weather App</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
            background-color: #f0f0f0;
        }
        .container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
            max-width: 400px;
            margin: auto;
        }
        input {
            padding: 10px;
            width: 80%;
            margin-bottom: 10px;
        }
        button {
            padding: 10px;
            background-color: #007bff;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        .result {
            margin-top: 20px;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Weather App</h2>
        <input type="text" id="location" placeholder="Enter your location">
        <button onclick="getWeather()">Get Weather</button>
        <div class="result" id="result"></div>
    </div>

    <script>
        async function getWeather() {
            const location = document.getElementById('location').value;
            if (!location) {
                alert("Please enter a location");
                return;
            }
            const apiKey = "fb5bc145d67b46bdbc854535251502";
            const url = `http://api.weatherapi.com/v1/current.json?key=${apiKey}&q=${location}&aqi=no`;
            try {
                const response = await fetch(url);
                const data = await response.json();
                document.getElementById('result').innerHTML = 
                    `Temperature in ${data.location.name}: ${data.current.temp_c}°C`;
            } catch (error) {
                document.getElementById('result').innerHTML = "Error fetching data. Try again!";
            }
        }
    </script>
</body>
</html>

