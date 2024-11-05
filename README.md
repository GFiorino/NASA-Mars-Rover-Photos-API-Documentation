# NASA Mars Rover Photos API Documentation

## Overview
This documentation provides developers with a comprehensive guide to retrieving Mars Rover images using NASA's public API. The guide covers essential endpoints, parameters, and examples to help developers access and utilize the API efficiently.

## Skills Used
- Markdown
- JSON
- GitHub

## Setup Instructions
1. Obtain an API key from NASA's API portal by signing up [here](https://api.nasa.gov/).
2. Place the API key in the `Authorization` header of your requests.

## Endpoints

### 1. Retrieve Rover Photos
- **Method**: GET
- **Endpoint URL**: `/rovers/{rover}/photos`
- **Description**: Fetches photos taken by a specific rover on Mars on a given Martian solar day (sol).
- **Parameters**:
  - `rover` (string): Name of the rover (e.g., `Curiosity`, `Opportunity`, `Spirit`).
  - `sol` (integer): The Martian solar day on which the photos were taken.
  - `camera` (optional, string): Specific camera used (e.g., `FHAZ` for Front Hazard Avoidance Camera).
    
- **Example Request**:
  ```http
  GET https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&api_key=DEMO_KEY
  ```



## Example Usage
To retrieve photos taken by the Curiosity rover on Martian sol 1000, make a GET request to the `/rovers/curiosity/photos` endpoint with your API key. The response will include image URLs, camera details, and additional metadata about the photos taken on that day.

![Sample Mars Rover Photo](https://github.com/GFiorino/NASA-Mars-Rover-Photos-API-Documentation/blob/main/images/Rover-Mars-photo-of-the-day.jpeg?raw=true)  
*Image credit: NASA*

### API Request-Response Flow
![API Request-Response Flow](https://github.com/GFiorino/NASA-Mars-Rover-Photos-API-Documentation/blob/main/Api-User-Server.png?raw=true)  
*Diagram illustrating the interaction between the User Application and NASA API Server.*

## Sample JSON Response
Below is an example JSON response you can expect from the API:

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
      "img_src": "http://mars.nasa.gov/msl-raw-images/proj/msl/redops/ods/surface/sol/01000/opgs/edr/fcam/FLB_486456045EDR_F0481570FHAZ00323M_.JPG",
      "earth_date": "2015-05-30",
      "rover": {
        "name": "Curiosity",
        "landing_date": "2012-08-06",
        "status": "active"
      }
    }
  ]
}
```
## FAQs
- **Q: How can I get an API key?**  
  **A:** Sign up for a free API key on NASA's [API portal](https://api.nasa.gov/).

- **Q: What is a Martian sol?**  
  **A:** A sol is a Martian solar day, approximately 24 hours and 39 minutes, used as a time unit for operations on Mars.

## Troubleshooting Tips
- **Authentication Errors**: If you encounter authentication issues, verify that your API key is correctly included in the `Authorization` header of your requests.
  
- **Empty Responses**: If no photos are returned, check that you’ve used the correct `rover` name and a valid `sol` parameter. Note that not all Martian days have photos available, so try different sol values if needed.
