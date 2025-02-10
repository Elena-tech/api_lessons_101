### **📌Building a Weather App with OpenWeather API (Step-by-Step)**  

#### **Title:** *Step-by-Step Guide to Creating a Weather Dashboard*  

#### **Content:**  
✅ **Goal:** Fetch and display real-time weather data from the **OpenWeather API**.  
✅ **Tech Stack:** Python (`requests`), JSON, and API calls.  

### **🔹 Step 1: Get an OpenWeather API Key**  
- **Sign up** at [OpenWeather API](https://home.openweathermap.org/api_keys).  
- Copy the **API key** for authentication.  

### **🔹 Step 2: Make an API Request in Python**  
- Fetch weather data for a city:
```python
import requests

api_key = "YOUR_API_KEY"
city = "London"
url = f"https://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric"

response = requests.get(url)
data = response.json()

# Extract relevant details
if "main" in data:
    temperature = data["main"]["temp"]
    weather_description = data["weather"][0]["description"]
    print(f"Weather in {city}: {temperature}°C, {weather_description}")
else:
    print("Error fetching weather data.")
```

### **🔹 Step 3: Process & Display Data**  
- Extract **temperature, humidity, and weather conditions**.  
- Handle errors gracefully (e.g., invalid city, API failures).  

### **🔹 Step 4: Bonus - Enhance with a GUI or Web App**  
- Use **Flask or Streamlit** to display weather details in a **user-friendly interface**.  
- Example: Create a simple **weather dashboard** in Streamlit.
```python
import streamlit as st

st.title("Weather Dashboard")

city = st.text_input("Enter city name:")
if city:
    response = requests.get(f"https://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric")
    data = response.json()
    if "main" in data:
        st.write(f"Temperature: {data['main']['temp']}°C")
        st.write(f"Weather: {data['weather'][0]['description']}")
    else:
        st.write("City not found!")
```

#### **Activity Suggestion:**  
🛠️ write a **Python script** that:  
   - Fetches and prints weather data for any **user-input city**.  
   - Enhances it by handling errors and adding **unit conversions (°C → °F)**.  

