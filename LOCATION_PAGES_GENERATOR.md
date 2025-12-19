# Location Pages Generator - Fresh Mutton Website

## Overview
This document provides instructions for generating individual location pages for all 16 service areas using the template from `gachibowli.html` and location data from `LOCATION_DATA.json`.

## Location Pages Status

### Completed (1/16)
- [x] Gachibowli (gachibowli.html) - DONE with full local SEO

### Remaining Locations (15)
1. HITEC City (hitec-city.html)
2. Kondapur (kondapur.html)
3. Madhapur (madhapur.html)
4. Mehadipatnam (mehadipatnam.html)
5. Tolichowki (tolichowki.html)
6. Manikonda (manikonda.html)
7. Narsingi (narsingi.html)
8. Financial District (financial-district.html)
9. Hafeezpet (hafeezpet.html)
10. Kukatpally (kukatpally.html)
11. Banjara Hills (banjara-hills.html)
12. Jubilee Hills (jubilee-hills.html)
13. Lingampally (lingampally.html)
14. Tellapur (tellapur.html)
15. Serilingampally (serilingampally.html)

## How to Generate Location Pages

### Method 1: Manual (For Each Location)

For each location in LOCATION_DATA.json:

1. Copy the gachibowli.html content
2. Replace:
   - Location name: "Gachibowli" → "[Location Name]"
   - Slug: "gachibowli" → "[location-slug]"
   - Coordinates: lat/lng values
   - Areas list: Sub-areas specific to location
   - Landmarks: Key landmarks for that location
   - Title and Meta tags with location keywords
   - Breadcrumb location name
   - All location-specific content

### Method 2: Automated (Recommended)

Create a Node.js script to generate all pages:

```javascript
const fs = require('fs');
const data = JSON.parse(fs.readFileSync('LOCATION_DATA.json', 'utf8'));

const locationTemplate = (loc) => `<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Fresh Organic Mutton Delivery in ${loc.name}, Hyderabad | Free Delivery</title>
<meta name="description" content="Fresh organic mutton same-day delivery in ${loc.name}, Hyderabad. Serving ${loc.areas.join(', ')}. 100% organic, FSSAI certified. Free delivery above ₹500.">
<meta name="keywords" content="mutton ${loc.name.toLowerCase()}, organic meat Hyderabad, fresh meat delivery, ${loc.areas.join(', ')}">
<meta name="geo.position" content="${loc.lat};${loc.lng}">
<meta name="geo.placename" content="${loc.name}, Hyderabad">
<meta name="geo.region" content="IN-TG">
<link rel="canonical" href="https://freshmutton.in/${loc.slug}.html">
<!-- [Include full CSS from gachibowli.html] -->
</head>
<body>
<!-- [Include Navigation, Hero, Content sections with location-specific data] -->
</body>
</html>`;

data.locations.forEach(loc => {
  const html = locationTemplate(loc);
  fs.writeFileSync(`${loc.slug}.html`, html);
  console.log(`Created ${loc.slug}.html`);
});
```

## Local SEO Optimization Included

Each location page includes:

1. **Geo-Targeting Meta Tags**
   - geo.position: Latitude/Longitude
   - geo.placename: Location name
   - geo.region: IN-TG (Telangana)

2. **Breadcrumb Navigation**
   - Home > Locations > [Location Name]
   - Schema markup for breadcrumbs

3. **Location-Specific Content**
   - Local landmarks
   - Sub-areas served
   - Localized keywords
   - Local business information

4. **SEO Elements**
   - Unique title tags with location keywords
   - Meta descriptions with area names
   - Internal linking to other locations
   - Structured data (LocalBusiness schema)
   - Canonical URLs

## Data Structure (LOCATION_DATA.json)

```json
{
  "locations": [
    {
      "name": "Location Name",
      "slug": "location-slug",
      "lat": "latitude",
      "lng": "longitude",
      "areas": ["Area 1", "Area 2", ...],
      "landmarks": ["Landmark 1", "Landmark 2", ...]
    }
  ]
}
```

## Next Steps

1. **Generate remaining 15 pages** using the automated method or template
2. **Update locations.html** to link to all 16 individual location pages
3. **Submit sitemap** to Google Search Console with all location pages
4. **Monitor rankings** for local keywords like "mutton [area name] Hyderabad"
5. **Update Google My Business** with address and hours for each service area

## Local SEO Keywords Per Location

- Gachibowli: "mutton Gachibowli", "DLF Cyber City", "Nanakramguda"
- HITEC City: "mutton HITEC City", "Inorbit Mall", "Raheja Mindspace"
- Kondapur: "mutton Kondapur", "Aparna Towers", "Kothaguda"
- [And so on for all locations...]

## Benefits

- **16 unique landing pages** for local search traffic
- **Breadcrumb navigation** for better UX and SEO
- **Geo-targeted content** for "near me" searches
- **Improved local rankings** across West Hyderabad
- **Higher click-through rates** from local SERPs
- **Better user engagement** with location-specific content
