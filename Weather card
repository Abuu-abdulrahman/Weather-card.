<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Live Weather Card</title>
  <style>
    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(to right, #74ebd5, #ACB6E5);
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .weather-card {
      background: white;
      border-radius: 20px;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
      width: 320px;
      text-align: center;
      padding: 25px;
      transition: transform 0.3s ease;
    }

    .weather-card:hover {
      transform: translateY(-8px);
    }

    .weather-icon img {
      width: 90px;
      height: 90px;
    }

    .temperature {
      font-size: 3em;
      font-weight: 600;
      margin: 10px 0;
    }

    .location {
      font-size: 1.2em;
      font-weight: 500;
      color: #444;
    }

    .condition {
      font-size: 1em;
      color: #777;
      margin-bottom: 15px;
    }

    .details {
      display: flex;
      justify-content: space-between;
      padding: 0 10px;
      color: #555;
    }

    .details div {
      text-align: center;
    }

    .details span {
      display: block;
      font-weight: 600;
    }

    .search {
      margin-bottom: 20px;
    }

    .search input {
      padding: 8px 12px;
      border: 1px solid #ccc;
      border-radius: 8px;
      width: 70%;
      outline: none;
    }

    .search button {
      padding: 8px 12px;
      background: #74ebd5;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      font-weight: bold;
    }

    .search button:hover {
      background: #ACB6E5;
    }
  </style>
</head>
<body>
  <div class="weather-card">
    <div class="search">
      <input type="text" id="cityInput" placeholder="Enter city name">
      <button onclick="getWeather()">Search</button>
    </div>

    <div class="weather-icon">
      <img id="icon" src="" alt="">
    </div>

    <div class="temperature" id="temp">--°C</div>
    <div class="location" id="city">--</div>
    <div class="condition" id="desc">--</div>

    <div class="details">
      <div>
        <span id="humidity">--%</span>
        Humidity
      </div>
      <div>
        <span id="wind">-- km/h</span>
        Wind
      </div>
    </div>
  </div>

  <script>
    const apiKey = "ec8159110e2dcc545cc6d7948954ddbd"; // ✅ your API key

    async function getWeather() {
      const city = document.getElementById('cityInput').value || "Saki";
      const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric&appid=${apiKey}`;

      try {
        const response = await fetch(url);
        const data = await response.json();

        if (data.cod !== 200) {
          alert("City not found!");
          return;
        }

        document.getElementById('city').textContent = data.name + ", " + data.sys.country;
        document.getElementById('temp').textContent = Math.round(data.main.temp) + "°C";
        document.getElementById('desc').textContent = data.weather[0].description;
        document.getElementById('humidity').textContent = data.main.humidity + "%";
        document.getElementById('wind').textContent = Math.round(data.wind.speed) + " km/h";
        document.getElementById('icon').src = `https://openweathermap.org/img/wn/${data.weather[0].icon}@2x.png`;
      } catch (error) {
        alert("Error fetching data!");
        console.error(error);
      }
    }

    // Load default city
    getWeather();
  </script>
</body>
</html>
