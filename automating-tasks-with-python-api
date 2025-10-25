import requests

# === CONFIGURATION ===
API_KEY = "472246a599af4e76d7b0a34d58298ca1"  # <-- Replace this
BASE_URL = "https://api.openweathermap.org/data/2.5/weather"

# === FUNCTION ===
def get_weather(city, units="metric"):
    params = {
        "q": city,
        "appid": API_KEY,
        "units": units  # "metric" (°C), "imperial" (°F), or "standard" (Kelvin)
    }

    response = requests.get(BASE_URL, params=params)
    
    if response.status_code != 200:
        print(f"Error fetching data: {response.status_code}")
        print(response.json())
        return
    
    data = response.json()

    # Extract weather info
    temperature = data["main"]["temp"]
    humidity = data["main"]["humidity"]
    wind_speed = data["wind"]["speed"]
    description = data["weather"][0]["description"].capitalize()

    print(f"\n🌤️ Weather in {city.title()}:")
    print(f"   Description: {description}")
    print(f"   Temperature: {temperature}° ({units})")
    print(f"   Humidity: {humidity}%")
    print(f"   Wind Speed: {wind_speed} {('m/s' if units=='metric' else 'mph')}")
    print("-------------------------------")

# === MAIN EXECUTION ===
if __name__ == "__main__":
    # Try different cities and parameters here
    get_weather("Provo", units="metric")      # Celsius
    get_weather("London", units="imperial")   # Fahrenheit
    get_weather("Tokyo", units="standard")    # Kelvin
