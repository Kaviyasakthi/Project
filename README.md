
import requests

API_KEY = "your_api_key"  # Get from https://openweathermap.org/api
BASE_URL = "http://api.openweathermap.org/data/2.5/weather"

def get_weather(city):
    params = {'q': city, 'appid': API_KEY, 'units': 'metric'}
    response = requests.get(BASE_URL, params=params)
    if response.status_code == 200:
        data = response.json()
        temp = data['main']['temp']
        desc = data['weather'][0]['description']
        humidity = data['main']['humidity']
        print(f"Weather in {city}: {temp}°C, {desc}, Humidity: {humidity}%")
    else:
        print("City not found!")

if __name__ == "__main__":
    city = input("Enter city name: ")
