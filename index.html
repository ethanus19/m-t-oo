<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!-- Leaflet.js CSS -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }
        body, html {
            height: 100%;
            overflow: hidden;
        }
        #map {
            height: 100%;
            width: 100%;
        }
        #info {
            position: absolute;
            bottom: 10px;
            left: 50%;
            transform: translateX(-50%);
            width: 90%;
            max-width: 400px;
            background: white;
            padding: 10px;
            border-radius: 10px;
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
            text-align: center;
            z-index: 1000;
        }
        #search-bar {
            position: absolute;
            top: 50px;
            left: 50%;
            transform: translateX(-50%);
            width: 90%;
            max-width: 300px;
            display: flex;
            gap: 5px;
            z-index: 1001;
        }
        input, button {
            padding: 8px;
            font-size: 14px;
            border: none;
            border-radius: 5px;
        }
        input {
            flex: 1;
            outline: none;
        }
        button {
            background: #007BFF;
            color: white;
            cursor: pointer;
        }
        #suggestions {
            position: absolute;
            top: 80px;
            left: 50%;
            transform: translateX(-50%);
            width: 90%;
            max-width: 300px;
            background: white;
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
            z-index: 1002;
            border-radius: 5px;
        }
        .suggestion {
            padding: 8px;
            cursor: pointer;
        }
        .suggestion:hover {
            background: #f1f1f1;
        }
    </style>
</head>
<body>

    <div id="search-bar">
        <input type="text" id="search" placeholder="Entrez une ville..." oninput="getCitySuggestions()">
        <button onclick="searchLocation()">🔍</button>
    </div>
    <div id="suggestions"></div>

    <div id="map"></div>

    <div id="info">
        <p id="temperature">🌡️ Température : -- °C</p>
        <p id="rain">🌧️ Précipitations : -- mm</p>
        <p id="wind">💨 Vent : -- km/h (--°)</p>
    </div>

    <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>

    <script>
        const apiKey = "ecd2b9ec5a987fd2421a072328e82e86";
        var map;
        var rainLayer;

        function initMap(latitude, longitude, zoomLevel = 12) {
            if (!map) {
                map = L.map('map', { zoomControl: false }).setView([latitude, longitude], zoomLevel);
            } else {
                map.setView([latitude, longitude], zoomLevel);
            }

            // Fond de carte épuré (sans mers territoriales ni routes maritimes)
            L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
                attribution: '&copy; OpenStreetMap contributors',
                maxZoom: 19
            }).addTo(map);

            // Couches météo (précipitations)
            rainLayer = L.tileLayer(`https://tile.openweathermap.org/map/precipitation_new/{z}/{x}/{y}.png?appid=${apiKey}`, {
                attribution: '© OpenWeatherMap',
                opacity: 0.6
            }).addTo(map);

            getWeatherData(latitude, longitude);
        }

        function getWeatherData(latitude, longitude) {
            const url = `https://api.openweathermap.org/data/2.5/weather?lat=${latitude}&lon=${longitude}&units=metric&lang=fr&appid=${apiKey}`;

            fetch(url)
                .then(response => response.json())
                .then(data => {
                    const temp = data.main.temp;
                    const windSpeed = (data.wind.speed * 3.6).toFixed(1);
                    const windDeg = data.wind.deg;
                    const rain = data.rain ? data.rain["1h"] || 0 : 0;

                    document.getElementById("temperature").innerText = `🌡️ Température : ${temp} °C`;
                    document.getElementById("rain").innerText = `🌧️ Précipitations : ${rain} mm`;
                    document.getElementById("wind").innerText = `💨 Vent : ${windSpeed} km/h (${windDeg}°)`;

                    updateRainColor(rain);
                })
                .catch(error => console.error("Erreur récupération météo", error));
        }

        // Mettre à jour la couleur de la couche de pluie selon l'intensité
        function updateRainColor(rain) {
            let color = "rgba(0, 255, 0, 0.5)"; // Vert (faible pluie)
            if (rain >= 2 && rain < 5) color = "rgba(255, 255, 0, 0.5)"; // Jaune (pluie modérée)
            if (rain >= 5 && rain < 10) color = "rgba(255, 165, 0, 0.6)"; // Orange (pluie forte)
            if (rain >= 10) color = "rgba(255, 0, 0, 0.7)"; // Rouge (très forte pluie)

            // Appliquer la couleur à la couche de précipitations
            rainLayer.setStyle({ opacity: 0.6, fillColor: color });
        }

        function getCitySuggestions() {
            const query = document.getElementById("search").value;
            if (query.length < 2) {
                document.getElementById("suggestions").innerHTML = "";
                return;
            }

            fetch(`https://api.openweathermap.org/geo/1.0/direct?q=${query},FR&limit=5&appid=${apiKey}`)
                .then(response => response.json())
                .then(data => {
                    let suggestionsHTML = "";
                    data.forEach(city => {
                        suggestionsHTML += `<div class="suggestion" onclick="selectCity('${city.name}', ${city.lat}, ${city.lon})">${city.name}</div>`;
                    });
                    document.getElementById("suggestions").innerHTML = suggestionsHTML;
                });
        }

        function selectCity(name, lat, lon) {
            document.getElementById("search").value = name;
            document.getElementById("suggestions").innerHTML = "";
            initMap(lat, lon, 14);
        }

        function searchLocation() {
            const location = document.getElementById("search").value;
            getCitySuggestions();
        }

        function getLocation() {
            navigator.geolocation.getCurrentPosition(
                (position) => initMap(position.coords.latitude, position.coords.longitude),
                () => initMap(48.8566, 2.3522) // Paris par défaut
            );
        }

        window.onload = getLocation;
    </script>

</body>
</html>
