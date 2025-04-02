# Weather Project
Sure! Let's work on a **Weather Project** where we fetch weather data from an API and present it in a user-friendly way. We’ll break down the project into the following steps:

### Steps for the Weather Project:
1. **API Integration**: We'll use a weather API (e.g., OpenWeatherMap) to fetch real-time weather data.
2. **Data Parsing**: We'll parse the data and extract key details such as temperature, humidity, and weather condition.
3. **User Input**: Allow the user to input the city name or location for which they want the weather information.
4. **Display Information**: Show the weather data in a readable format.

### Required Libraries:
1. **Requests**: To make API calls and fetch data.
2. **JSON**: To parse the JSON response from the API.
3. **Geopy (optional)**: To get weather data based on location if needed.

### Step 1: Get API Key
First, you'll need an API key from [OpenWeatherMap](https://openweathermap.org/). Once you register, you can get your free API key.

### Step 2: Install Required Libraries

If you don’t already have `requests` installed, you can install it using `pip`:

```bash
pip install requests
```

### Step 3: Write the Code

Here’s a basic Python script that fetches the weather details for a given city:

```python
import requests

# Define your API key (Get this from OpenWeatherMap after registering)
API_KEY = "your_api_key_here"  # Replace with your OpenWeatherMap API key
BASE_URL = "http://api.openweathermap.org/data/2.5/weather"

# Function to fetch weather details
def get_weather(city):
    # Construct the URL to make the request
    complete_url = f"{BASE_URL}?q={city}&appid={API_KEY}&units=metric"  # 'metric' for Celsius, 'imperial' for Fahrenheit
    
    # Make the GET request to the API
    response = requests.get(complete_url)
    
    # Check if the response is successful
    if response.status_code == 200:
        data = response.json()
        
        # Extract relevant information
        main = data['main']
        weather = data['weather'][0]
        
        temperature = main['temp']
        humidity = main['humidity']
        weather_description = weather['description']
        
        # Output the weather information
        print(f"Weather in {city}:")
        print(f"Temperature: {temperature}°C")
        print(f"Humidity: {humidity}%")
        print(f"Condition: {weather_description.capitalize()}")
        
    else:
        print("City not found or invalid API request.")

# Main program loop
if __name__ == "__main__":
    city = input("Enter the city name: ")
    get_weather(city)
```

### Explanation of the Code:
1. **API Request**: We use the `requests` library to make an HTTP GET request to OpenWeatherMap's API.
2. **API Response**: The response is in JSON format, which we parse using the `.json()` method.
3. **Extract Data**: We extract the temperature, humidity, and weather condition from the JSON response.
4. **Display Data**: The information is printed to the console in a user-friendly format.

### Step 4: Run the Program
When you run this Python script, it will ask you to enter the name of a city. After you input the city, it will display the weather information, including:
- **Temperature** (in Celsius)
- **Humidity** (as a percentage)
- **Weather condition** (e.g., clear, rainy, cloudy)

### Example Output:
```text
Enter the city name: London
Weather in London:
Temperature: 14.6°C
Humidity: 82%
Condition: Clear sky
```

### Step 5: Error Handling
You can improve the program by adding error handling, such as checking if the user enters a valid city name and handling API rate limits. You can also customize the output format and add additional features such as:
- **5-day forecast**
- **Displaying results for multiple cities**
- **Weather icon based on condition**

Let me know if you'd like to add any specific features or need help with additional functionalities!
