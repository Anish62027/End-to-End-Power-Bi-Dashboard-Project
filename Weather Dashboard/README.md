

# 🌦️ Power BI Weather Dashboard using WeatherAPI

This project shows how to create a **live weather and air quality dashboard** in Power BI using data from [WeatherAPI.com](https://www.weatherapi.com/). It's simple, useful, and can be easily customized!

---

## ✅ Why WeatherAPI?

WeatherAPI gives live, historical, and forecast weather data in **JSON format**, which is perfect for Power BI. It also provides **Air Quality Index (AQI)** data.

---

## 📌 Project Highlights

✅ Real-time weather data from API  
✅ Displays temperature, humidity, wind speed, and weather condition  
✅ Shows AQI levels (pm2.5, co, no2, etc.)  
✅ DAX-based AQI Status, Color Code, and Suggestions  
✅ Filter for different cities  
✅ User-friendly and dynamic design

---

## 🧰 Requirements

- Free or paid account at [WeatherAPI.com](https://www.weatherapi.com/)
- Power BI Desktop
- Basic knowledge of Power BI

---

## 🔑 Step 1: Get Your API Key

1. Go to [WeatherAPI.com](https://www.weatherapi.com/), sign up and log in.
2. Copy your **API Key** from your dashboard.

---

## 🔗 Step 2: Create the API URL

Use the below link format to get current weather:

```

[https://api.weatherapi.com/v1/current.json?key=YOUR\_API\_KEY\&q=CITY\_NAME](https://api.weatherapi.com/v1/current.json?key=YOUR_API_KEY&q=CITY_NAME)

````

Replace:
- `YOUR_API_KEY` with your real API key  
- `CITY_NAME` with the name of the city (like `Delhi` or `Mumbai`)

---

## 📥 Step 3: Load Data in Power BI

1. Open Power BI Desktop
2. Click **Get Data → Web**
3. Paste the API URL
4. Click **OK**

---

## 🔄 Step 4: Transform the Data

In the Power Query Editor:
- Expand the `current` record
- Expand nested fields like `condition` and `air_quality`
- Rename columns for clarity
- Click **Close & Apply**

---

## 📊 Step 5: Create the Dashboard

Add the following visuals:
- **Cards** for temperature, humidity, etc.
- **Gauges** for wind speed
- **Line/Bar Charts** for changes over time
- **Slicers** for different cities

---

## 🎨 Step 6: Add Styling

- Add weather icons (sun, cloud, etc.)
- Use **Map Visual** to show locations
- Let users pick a city from a dropdown slicer

---

## 🌫️ Step 7: Add AQI Measures

You can visualize **Air Quality Index** by using reusable DAX measures. Below are templates:

### 🟥 AQI Color

```DAX
AQI Color = 
VAR AQI = ROUND(SELECTEDVALUE('Current'[current.air_quality.COLUMN_NAME]), 0)
RETURN 
SWITCH(
    TRUE(),
    AQI <= 50, "#43d946", 
    AQI <= 100, "#fff570", 
    AQI <= 150, "#ff9800", 
    AQI <= 200, "#d99343", 
    AQI <= 300, "#ff5b0f", 
    "#d95243"
)
````

### 💬 AQI Suggestion

```DAX
AQI Suggestion = 
VAR AQI = ROUND(SELECTEDVALUE('Current'[current.air_quality.COLUMN_NAME]), 0)
RETURN 
SWITCH(
    TRUE(),
    AQI <= 50, "Air is clean and healthy",
    AQI <= 100, "Acceptable air quality",
    AQI <= 150, "Sensitive groups should be careful",
    AQI <= 200, "Avoid staying out too long",
    AQI <= 300, "Stay inside if possible",
    "Very bad air quality"
)
```

### 📈 AQI Status

```DAX
AQI Status = 
VAR AQI = ROUND(SELECTEDVALUE('Current'[current.air_quality.COLUMN_NAME]), 0)
RETURN 
SWITCH(
    TRUE(),
    AQI <= 50, "Good",
    AQI <= 100, "Moderate",
    AQI <= 150, "Unhealthy for Sensitive",
    AQI <= 200, "Unhealthy",
    AQI <= 300, "Very Unhealthy",
    "Hazardous"
)
```

Replace `COLUMN_NAME` with pollutants like:

* `pm2_5`
* `co`
* `no2`
* `so2`
* `o3`

---

## 🚀 Conclusion

With just a few steps, you can build a **live weather dashboard** using Power BI and WeatherAPI. Adding AQI helps provide more value to users.

💡 Tip: Save your DAX formulas as templates so you can easily add more pollutants later.

---

### 📁 Project Structure

```bash
📦PowerBI-WeatherDashboard/
 ┣ 📄 README.md
 ┣ 📁 visuals/ (optional icons/images)
 ┣ 📁 pbix-files/
 ┃ ┗ 📄 WeatherDashboard.pbix
```

---

## 🔗 Useful Links

* [WeatherAPI Docs](https://www.weatherapi.com/docs/)
* [Download Power BI](https://powerbi.microsoft.com/)
* [Download Power BI Desktop](https://powerbi.microsoft.com/desktop)
* [Microsoft Power BI Docs](https://learn.microsoft.com/en-us/power-bi/)

```

## 👨‍💻 Created by [Anish62027](https://github.com/Anish62027)

Give this repo a ⭐ if you like it or want to fork and improve it!
[WeatherAPI Docs](https://www.weatherapi.com/docs/)

```

---
