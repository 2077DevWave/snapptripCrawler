# 🚌 Bus Availability API
This API allows users to check bus availability between two cities in Iran for a specific date. It fetches data from SnappTrip's public API and returns available buses based on the provided origin, destination, and date

## 🚀 Quick Start

### Base URL
```
https://snapptripcrawler.sideco.ir/
```

### Example Request
```
GET https://snapptripcrawler.sideco.ir/?origin=Tehran&destination=Fasa&date=2025-04-20
```

### Query Parameters
 `origin` (string, required): Name of the origin city (e.g., `Tehran`).
 
 `destination` (string, required): Name of the destination city (e.g., `Shiraz`).
 
 `date` (string, required): Travel date in `YYYY-MM-DD` format (e.g., `2025-04-20`).

### Response
Returns a JSON array of available buses with details such as departure time, price, and bus typ.

```json
[
  {
    "busType": "VIP",
    "departureTime": "2025-04-20T08:00:00",
    "price": 150000,
    "availableSeats": 10,
    "origin": "Tehran",
    "destination": "Fasa"
  },
]
```

## 🔍 How It Works

1. **City Code Retrieval**: The API queries SnappTrip's endpoint to fetch the city code corresponding to the provided `origin` and `destination` names. It performs a case-insensitive match against the `cityEn` fied.

2. **Bus Availability Fetching**: Using the retrieved city codes and the provided date, the API constructs a request to SnappTrip's availability endpoint to fetch available buss.

3. **Response Delivery**: The API returns the fetched data directly to the user in JSON formt.

## ⚠️ Error Handling
- If any of the required query parameters (`origin`, `destination`, or `date`) are missing, the API responds wih:

```json
  {
    "error": "Missing origin, destination, or date parameter."
  }
```
- if the provided city names do not match any known cities, the API responds wih:
  
```json
  {
    "error": "City not found."
  }
```

## 📄 Licese

This project is licensed under the MIT Licnse.
