## Demo Case: Selling an Office Chair via Voice (SF Bay Area)

**Scenario:** A user in San Francisco wants to sell their used office chair quickly. They send a casual voice message to the Babel Engine.

### 1. User Input (Unstructured Voice Transcript)
> "Yo, I'm listing my Herman Miller Aeron chair. It's a size B. The mesh is still perfect, but the left armrest is kinda scuffed up from hitting my desk. Asking $450. You gotta pick it up from my place in SoMa, San Francisco. Need it gone by weekend."

### 2. Babel Processing Pipeline
* **Entity Detection:** Herman Miller Aeron Chair (Size B).
* **Condition Assessment:** "Mesh perfect" + "armrest scuffed" -> Mapped to **Grade B (Minor Signs of Wear)**.
* **Pricing extraction:** $450 USD.
* **Location grounding:** SoMa, San Francisco -> Resolved to GPS coordinates `37.77, -122.41`.
* **Urgency signal:** "by weekend" -> Added temporal context.

### 3. JSON Output (Standardized)
```json
{
  "@context": "[https://schema.org/](https://schema.org/)",
  "@type": "Product",
  "name": "Herman Miller Aeron Chair - Size B",
  "description": "Used Herman Miller Aeron (Size B). Mesh fabric in excellent condition. Minor scuffs present on the left armrest.",
  "spatialCoverage": {
    "@type": "Place",
    "name": "SoMa, San Francisco, CA",
    "geo": {
      "@type": "GeoCoordinates",
      "latitude": "37.7749",
      "longitude": "-122.4194"
    }
  },
  "offers": {
    "@type": "Offer",
    "price": 450.00,
    "priceCurrency": "USD",
    "availability": "[https://schema.org/InStock](https://schema.org/InStock)",
    "itemCondition": "Grade B",
    "priceValidUntil": "2025-10-12T23:59:59"
  },
  "keywords": ["Office Chair", "Herman Miller", "Aeron", "Used Furniture", "SF Bay Area"]
}
