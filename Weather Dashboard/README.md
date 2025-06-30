Here’s a rewritten version of your **Power BI Weather Dashboard** project README in a clean, engaging, and professional tone. It improves clarity, formatting, and readability while keeping your original structure and technical details intact.

---

# 🌤️ Power BI Live Weather & AQI Dashboard with WeatherAPI

Create a **real-time weather and air quality monitoring dashboard** in Power BI using data from [WeatherAPI.com](https://www.weatherapi.com/). This project is simple, practical, and highly customizable—perfect for both beginners and experienced Power BI users.

---

## ✅ Why Choose WeatherAPI?

[WeatherAPI](https://www.weatherapi.com/) provides comprehensive weather data, including:

* Current conditions
* Forecasts
* Historical weather
* **Air Quality Index (AQI)**
  All available in **JSON format**, which integrates seamlessly with Power BI.

---

## 🌟 Key Features

* 🔄 **Live weather data** from the API
* 🌡️ Display of temperature, humidity, wind speed, and weather condition
* 🏭 AQI visualizations: PM2.5, CO, NO2, SO2, O3, etc.
* 🎯 **Dynamic DAX Measures** for:

  * AQI color coding
  * Health suggestions
  * AQI status labels
* 🌍 Multi-city selection with slicers
* ✨ Visually appealing and user-friendly interface

---

## 🧰 What You’ll Need

* A **free or paid** [WeatherAPI.com](https://www.weatherapi.com/) account
* Power BI Desktop
* Basic understanding of Power BI & Power Query

---

## 🔑 Step 1: Get Your API Key

1. Sign up at [WeatherAPI.com](https://www.weatherapi.com/)
2. Copy your personal **API Key** from your dashboard

---

## 🔗 Step 2: Build the API URL

Use the following format:

```
https://api.weatherapi.com/v1/current.json?key=YOUR_API_KEY&q=CITY_NAME
```

Replace:

* `YOUR_API_KEY` with your actual key
* `CITY_NAME` with a city (e.g., `Delhi`, `Mumbai`)

---

## 📥 Step 3: Load Data in Power BI

1. Open Power BI Desktop
2. Go to **Get Data → Web**
3. Paste your API URL
4. Click **OK**

---

## 🔧 Step 4: Transform Data

In **Power Query Editor**:

* Expand the `current` record
* Expand nested fields like `condition` and `air_quality`
* Rename columns for readability
* Click **Close & Apply**

---

## 📊 Step 5: Build the Dashboard

Create the following visuals:

* **Cards** → Temperature, Humidity, Condition
* **Gauges** → Wind Speed
* **Bar/Line Charts** → Time series (optional with scheduled refresh or static data)
* **Slicers** → City selection

---

## 🎨 Step 6: Design & Style

* Add weather icons (sun, clouds, etc.)
* Use a **Map visual** to display city locations
* Style your dashboard using themes, color gradients, and borders for clarity

---

## 🌫️ Step 7: Add AQI DAX Measures

### 🟥 AQI Color Code

```DAX
AQI Color = 
VAR AQI = ROUND(SELECTEDVALUE('Current'[current.air_quality.COLUMN_NAME]), 0)
RETURN 
SWITCH(
    TRUE(),
    AQI <= 50, "#43d946",        // Good
    AQI <= 100, "#fff570",       // Moderate
    AQI <= 150, "#ff9800",       // Unhealthy for Sensitive
    AQI <= 200, "#d99343",       // Unhealthy
    AQI <= 300, "#ff5b0f",       // Very Unhealthy
    "#d95243"                    // Hazardous
)
```

### 💬 AQI Suggestion Message

```DAX
AQI Suggestion = 
VAR AQI = ROUND(SELECTEDVALUE('Current'[current.air_quality.COLUMN_NAME]), 0)
RETURN 
SWITCH(
    TRUE(),
    AQI <= 50, "Air is clean and healthy",
    AQI <= 100, "Acceptable air quality",
    AQI <= 150, "Sensitive groups should be cautious",
    AQI <= 200, "Limit outdoor activities",
    AQI <= 300, "Prefer staying indoors",
    "Very poor air quality, avoid going out"
)
```

### 📈 AQI Status Label

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

## 🚀 Final Thoughts

You now have a fully functional **live weather and AQI dashboard** in Power BI powered by WeatherAPI. This is a great starting point to explore other integrations and build advanced analytics projects.

> 💡 **Tip**: Save the DAX measures as templates for easy reuse with other pollutants.

---

## 📁 Project Structure

```bash
📦PowerBI-WeatherDashboard/
 ┣ 📄 README.md
 ┣ 📁 visuals/            # (icons/images for the dashboard)
 ┣ 📁 pbix-files/
 ┃ ┗ 📄 WeatherDashboard.pbix
```

---

## 🔗 Helpful Resources

* [WeatherAPI Documentation](https://www.weatherapi.com/docs/)
* [Download Power BI](https://powerbi.microsoft.com/)
* [Power BI Desktop](https://powerbi.microsoft.com/desktop)
* [Microsoft Learn - Power BI](https://learn.microsoft.com/en-us/power-bi/)

---

## 👨‍💻 Created by [Anish62027](https://github.com/Anish62027)

⭐ Star this repo if you find it helpful or want to fork it!

---

## 📷 Dashboard Preview

![Weather Dashboard Preview](https://github.com/Anish62027/End-to-End-Power-Bi-Dashboard-Project/blob/main/Weather%20Dashboard/WhatsApp%20Image%202025-06-24%20at%2019.41.54_8bd15369.jpg?raw=true)

![Weather Dashboard Preview](https://github.com/Anish62027/End-to-End-Power-Bi-Dashboard-Project/blob/main/Weather%20Dashboard/WhatsApp%20Image%202025-06-24%20at%2019.47.19_d9d229d8.jpg?raw=true)


---

Would you like a Markdown version you can copy directly for GitHub or a LinkedIn post template too?
