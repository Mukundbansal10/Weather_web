# Weather Webpage

Welcome to the Weather Webpage project! This is a simple web application that displays the weather of a specified city using an external API.

## Features

- Get current weather information for any city.
- User-friendly interface.
- Displays temperature, weather conditions, humidity, and wind speed.

## Installation

1. **Clone this repository**:
   ```bash
   git clone https://github.com/Mukundbansal10/Weather_web.git
   ```

2. **Navigate to the project directory**:
   ```bash
   cd Weather_web
   ```

3. **Open `index.html` in your browser**:
   - Simply double-click on the `index.html` file or open it using your browser.

## Usage

1. Enter the name of the city in the input field.
2. Click the "Get Weather" button.
3. The weather information for the specified city will be displayed.

## Project Structure

```
- Weather_web/
  - css/
    - styles.css
  - js/
    - script.js
  - index.html
```

## Files Explained

- **css/**: Contains the CSS file for styling the webpage.
  - **styles.css**: The CSS file that styles the HTML elements.
- **js/**: Contains the JavaScript file for fetching and displaying the weather information.
  - **script.js**: The JavaScript file that makes the API call and updates the DOM with the weather data.
- **index.html**: The main HTML file that structures the webpage.

## Example Code

### index.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Weather Webpage</title>
  <link rel="stylesheet" href="css/styles.css">
</head>
<body>
  <div class="container">
    <h1>Weather Webpage</h1>
    <input type="text" id="city" placeholder="Enter city name">
    <button id="getWeather">Get Weather</button>
    <div id="weatherInfo">
      <p id="temperature"></p>
      <p id="condition"></p>
      <p id="humidity"></p>
      <p id="wind"></p>
    </div>
  </div>
  <script src="js/script.js"></script>
</body>
</html>
```

### styles.css
```css
body {
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
  text-align: center;
  padding: 50px;
}

.container {
  background-color: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  max-width: 400px;
  margin: auto;
}

input {
  padding: 10px;
  font-size: 16px;
  width: 80%;
  margin-bottom: 10px;
}

button {
  padding: 10px;
  font-size: 16px;
  cursor: pointer;
}

#weatherInfo p {
  margin: 5px 0;
}
```

### script.js
```javascript
document.getElementById('getWeather').addEventListener('click', function() {
  const city = document.getElementById('city').value;
  const apiKey = 'YOUR_API_KEY'; // Replace with your weather API key
  fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`)
    .then(response => response.json())
    .then(data => {
      document.getElementById('temperature').innerText = `Temperature: ${data.main.temp}°C`;
      document.getElementById('condition').innerText = `Condition: ${data.weather[0].description}`;
      document.getElementById('humidity').innerText = `Humidity: ${data.main.humidity}%`;
      document.getElementById('wind').innerText = `Wind Speed: ${data.wind.speed} m/s`;
    })
    .catch(error => {
      console.error('Error fetching weather data:', error);
      alert('Failed to fetch weather data. Please try again.');
    });
});
```

## Contributions

Contributions are welcome! If you have suggestions for improvements or new features, feel free to fork this repository and create a pull request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Thanks to the [OpenWeather API](https://openweathermap.org/api) for providing the weather data.
