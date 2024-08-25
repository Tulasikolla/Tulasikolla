// Weather Report Program

// Import required modules
const readline = require('readline');

// Define weather conditions
const weatherConditions = {
  "sunny": "Sunny",
  "cloudy": "Cloudy",
  "rainy": "Rainy",
  "flood": "Flood Warning"
};

// Define humidity levels
const humidityLevels = {
  "low": 0,
  "medium": 50,
  "high": 80
};

// Function to get weather condition based on humidity
function getWeatherCondition(humidity) {
  if (humidity < humidityLevels.medium) {
    return weatherConditions.sunny;
  } else if (humidity < humidityLevels.high) {
    return weatherConditions.cloudy;
  } else {
return weatherConditions.rainy;
  }
}

// Function to check for flood warning
function checkForFlood(humidity, rainfall) {
  if (humidity > humidityLevels.high && rainfall > 10) {
    return weatherConditions.flood;
  } else {
    return "";
  }
}

// Create a readline interface
const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});

// Ask for humidity and rainfall levels
rl.question('Enter humidity level (0-100): ', (humidity) => {
  rl.question('Enter rainfall level (mm): ', (rainfall) => {
    // Convert inputs to numbers
    humidity = parseInt(humidity);
    rainfall = parseInt(rainfall);
 // Get weather condition and flood warning
    let weatherCondition = getWeatherCondition(humidity);
    let floodWarning = checkForFlood(humidity, rainfall);

    // Display results
    console.log(`Weather Condition: ${weatherCondition}`);
    console.log(`Flood Warning: ${floodWarning}`);

    // Close readline interface
    rl.close();
  });
});

