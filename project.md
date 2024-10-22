# Mars Rover Photos API Documentation

## Overview
The Mars Rover Photos API allows users to retrieve images taken by NASA's Curiosity, Opportunity, and Spirit rovers on Mars.

## Authentication
To access the API, you need an API key. Sign up at [NASA's API Portal](https://api.nasa.gov/).

## Example Request
GET https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&api_key=YOUR_API_KEY

## Parameters
- **`sol`**: Martian day for the rover (`integer`).
- **`api_key`**: Your unique API key.
- **Optional Parameters**:
   - **`camera`**: Limit results to specific cameras.

## Response Structure
The API responds with a JSON array:
- **`id`**: Unique photo identifier.
- **`img_src`**: URL of the photo.
- **`camera`**: Information about the camera used.

## Example Response
```json
{
    "photos": [
        {
            "id": 102693,
            "sol": 1000,
            "camera": {
                "name": "FHAZ",
                "full_name": "Front Hazard Avoidance Camera"
            },
            "img_src": "http://mars.jpl.nasa.gov/...",
            "earth_date": "2015-05-30"
        }
    ]
}
```
## Error Handling
- **Invalid API Key**: Returns `403 Forbidden`.
- **Missing Parameters**: Returns `400 Bad Request`.

## Common Use Cases
- **Fetch daily Mars photos**: Retrieve images from the rover for a specified Martian day.
- **Filter by Camera**: Get images taken by specific cameras.

## Troubleshooting
- **Make sure the API key is valid.**
- **Check parameter formats** (e.g., `sol` should be an integer).
