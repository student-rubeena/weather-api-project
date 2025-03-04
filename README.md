# weather-api-project
WeatherNow is a simple and interactive weather-fetching web application built using HTML, CSS, and JavaScript. It integrates with a weather API to fetch real-time weather data based on user input.
----> code
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>weather</title>
    <link rel="stylesheet" href="weather.css">
</head>
<body>
    <div class="card">
        <div class="search">
            <input type="text" placeholder="enter city name" spellcheck="false">
            <button><img src="assests/weather images/search.png"></button>
        </div>
        <div class="weather">
            <img src="assests/weather images/rain.png" class="weather-icon">
            <h1 class="temp">22°c</h1>
            <h2 class="city">New York</h2>
            <div class="details">
                <div class="col">
                    <img src="assests/weather images/humidity.png">
                    <div>
                        <p class="humidity">50%</p>
                        <p>humidity</p>
                    </div>
                </div>
                <div class="col">
                    <img src="assests/weather images/wind.png">
                    <div>
                        <p class="wind">15 km/h</p>
                        <p>Wind speed</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <script src="weather.js"></script>
</body>
</html>

* {
    margin: 0;
    padding: 0;
    font-family: 'poppins', sans-serif;
    box-sizing: border-box;
}
body{
    background: #222;
}
.card{
    width: 90%;
    max-width: 470px;
    background: linear-gradient(135deg, #00feba, #5b548a);
    color: #fff;
    margin: 100px auto 0;
    border-radius: 20px;
    padding: 40px 35px;
    text-align: center;
}
.search{
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.search input{
    border: 0;
    outline: 0;
    background: #ebfffc;
    color: #555;
    padding: 10px 25px;
    height: 60px;
    border-radius: 30px;
    flex: 1;
    margin-right: 16px;
    font-size: 18px;
}
.search button{
    border: 0;
    outline: 0;
    background: #ebfffc;
    border-radius: 50%;
    width: 60px;
    height: 60px;
    cursor: pointer;
}
.search button img{
    width: 16px;
}
.weather-icon{
    width: 170px;
    margin-top: 30px;

}
.weather h1{
    font-size: 80px;
    font-weight: 500;
}
.weather h2{
    font-size: 45px;
    font-weight: 400;
    margin-top: -10px;
}
.details{
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 20px;
    margin-top: 50px;
}
.col{
    display: flex;
    align-items: center;
    text-align: left;
}
.col img{
    width: 40px;
    margin-right: 10px;
}
.humidity, .wind{
    font-size: 28px;
    margin-top: -6px;
}
@media (max-width: 320px) {
    .search{
        width: 100%;
    }
    .search input{
        border: 0;
        outline: 0;
        background: #ebfffc;
        color: #555;
        padding: 10px 25px;
        height: 40px;
        border-radius: 30px;
        flex: 1;
        margin-right: 8px;
        font-size: 12px;
    }
    .search button img{
        width: 20px;
    }
    .col{
        display: flex;
        align-items: center;
        text-align: left;
    }
    .col img{
        width: 20px;
        margin-right: 10px;
    }
    .humidity, .wind{
        font-size: 20px;
        margin-top: -6px;
    }
}
const apiKey = "7280c55ff00b562f6cbff5901c14ef34";
const apiUrl= "https://api.openweathermap.org/data/2.5/weather?&units=metric&q=";
const searchBox = document.querySelector(".search input");
const searchBtn = document.querySelector(".search button");
const weatherIcon = document.querySelector(".weather-icon");

async function checkWeather(city) {
    const response = await fetch(apiUrl + city + `&appid=${apiKey}`);
    var data = await response.json();
    console.log("wheater", data);

document.querySelector(".city").innerHTML = data.name;
document.querySelector(".temp").innerHTML = data.main.temp + "°c";
document.querySelector(".humidity").innerHTML = data.main.humidity + "%" ;
document.querySelector(".wind").innerHTML = data.wind.speed + " km/h";

if(data.weather[0].main == "Clouds") {
    weatherIcon.src = "assests/weather images/clouds.png";
}
else if(data.weather[0].main == "Rain") {
    weatherIcon.src = "assests/weather images/rain.png";
}
else if(data.weather[0].main == "Drizzle") {
    weatherIcon.src = "assests/weather images/drizzle.png";
}
else if(data.weather[0].main == "Mist") {
    weatherIcon.src = "assests/weather images/mist.png";
}
}


 searchBtn.addEventListener("click", ()=> {
    checkWeather(searchBox.value);
 })

--->Features

Search for real-time weather data by city name

Display temperature, humidity, and wind speed

Visually appealing UI with smooth design

API integration for accurate weather details

---->Technologies Used

HTML

CSS

JavaScript

OpenWeatherMap API (or any other weather API used)

----->Installation & Setup

Clone the repository:

git clone https://github.com/yourusername/weathernow.git

Navigate to the project directory:

cd weathernow

Open weather.html in a browser to run the project.

API Integration

This project fetches weather data from OpenWeatherMap API.

You need to obtain an API key from OpenWeatherMap and replace it in your JavaScript file.

----->How to Use

Enter the city name in the search bar.

Click the search button to fetch weather details.

View the temperature, humidity, and wind speed in an interactive card.

----->Future Enhancements

Add a 5-day weather forecast feature.

Implement geolocation-based weather fetching.

Improve UI with more animations and styling.

----->Screenshots
![Screenshot (47)](https://github.com/user-attachments/assets/2090e992-439a-4a70-aecc-0541d92b8509)



----->License

This project is open-source and available under the MIT License.
