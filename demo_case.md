# Demo Cases: Babel in Action

This document demonstrates how **Project Babel** standardizes diverse real-world signals into AI-readable JSON. 

We cover 5 core scenarios:
1.  **Standard Goods** (Second-hand Furniture)
2.  **Perishable Goods** (Fresh Catch/Market)
3.  **Dynamic Mobility** (Ride Sharing)
4.  **Real-time Status** (Crowd/Queue)
5.  **Resource Sharing** (EV Charging)

---

## Case 1: Selling an Office Chair (Standard Goods)
**📍 Location:** San Francisco, USA
**🎙️ Input:** "I'm listing my Herman Miller Aeron chair. Size B. Mesh is perfect, but left armrest is scuffed. Asking $450. Pick up at SoMa."

**📄 JSON Output:**
```json
{
  "@context": "https://schema.org/",
  "@type": "Product",
  "name": "Herman Miller Aeron Chair - Size B",
  "description": "Used Herman Miller Aeron. Minor scuffs on armrest.",
  "spatialCoverage": {
    "@type": "Place",
    "name": "SoMa, San Francisco",
    "geo": { "latitude": "37.77", "longitude": "-122.41" }
  },
  "offers": {
    "@type": "Offer",
    "price": 450.00,
    "priceCurrency": "USD",
    "itemCondition": "Grade B"
  }
}
```

---

## Case 2: Fresh Catch at the Dock (Perishable Goods)
**📍 Location:**  Gloucester Harbor, MA, USA 
**🎙️ Input:** "Just docked at Pier 4. We have 50 lbs of fresh Mackerel, caught this morning. $8 a pound. First come first serve, we leave in 2 hours."
**⚙️ Babel Insight:**  Captures "Perishability" and "Urgency".

**📄 JSON Output:** 
```json
{
  "@context": "https://schema.org/",
  "@type": "Product",
  "category": "Seafood",
  "name": "Fresh Mackerel (Morning Catch)",
  "spatialCoverage": {
    "@type": "Place",
    "name": "Pier 4, Gloucester Harbor",
    "geo": { "latitude": "42.61", "longitude": "-70.66" }
  },
  "offers": {
    "@type": "Offer",
    "price": 8.00,
    "priceCurrency": "USD",
    "unitCode": "LBR", 
    "inventoryLevel": "50 lbs",
    "validThrough": "2025-10-24T12:00:00-05:00" 
  }
}
```

---

## Case 3: Hitching a Ride (Dynamic Mobility)
**📍 Location:** Beijing, China 
**🎙️ Input:** "I'm driving from Guomao to the Airport right now. I have 2 empty seats. Just share the gas money, maybe 30 RMB. Leaving in 5 mins."
**⚙️ Babel Insight:** Maps "Origin -> Destination" and "Capacity".

**📄 JSON Output:**
```json
{
  "@context": "https://schema.org/",
  "@type": "TravelAction",
  "name": "Ride Share: Guomao to PEK Airport",
  "agent": { "@type": "Person", "name": "Anonymous Driver" },
  "fromLocation": "Guomao CBD",
  "toLocation": "Beijing Capital Airport (PEK)",
  "startTime": "2025-10-24T14:05:00+08:00",
  "object": {
    "@type": "TransportationService",
    "vehicleType": "Car",
    "availableSeats": 2,
    "price": "30 CNY"
  }
}
```

---

## Case 4: Coffee Shop Queue (Real-time Status)
**📍 Location:** Shibuya, Tokyo, Japan 
**🎙️ Input:** "Starbucks at Shibuya Crossing is absolutely packed. Line is out the door, wait time is at least 20 mins."

**📄 JSON Output:**
```json
{
  "@context": "https://schema.org/",
  "@type": "Service",
  "name": "Starbucks - Shibuya Crossing",
  "status": {
    "@type": "RealTimeStatus",
    "crowdLevel": "High",
    "estimatedWaitTime": "PT20M"
  }
}
```

---

## Case 5: Sharing EV Charger (Resource Sharing)
**📍 Location:** London, UK 
**🎙️ Input:** "My private driveway EV charger is available for the next 4 hours. 5 pounds flat rate."

**📄 JSON Output:**
```json
{
  "@context": "https://schema.org/",
  "@type": "CivicStructure",
  "name": "Private EV Charging Spot",
  "offers": {
    "@type": "Offer",
    "price": 5.00,
    "priceCurrency": "GBP",
    "validThrough": "T+4H"
  }
}
```
