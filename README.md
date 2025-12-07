# MoviesDatabase API Documentation

## API Overview
The MoviesDatabase API provides access to extensive movie-related data such as movie details, cast information, ratings, posters, and search capabilities. It allows developers to retrieve structured movie information programmatically, making it useful for film apps, recommendation systems, and data analysis.

## Version
**API Version:** v1

## Available Endpoints
Here are the main endpoints available:

- **/titles** – Retrieve a list of movie titles with filtering options.
- **/titles/{id}** – Get detailed information about a specific movie by its ID.
- **/titles/search** – Search for movies by keywords, genre, or year.
- **/titles/{id}/cast** – Fetch cast and crew details for a specific movie.
- **/titles/{id}/ratings** – Retrieve ratings and score breakdown for a title.
- **/titles/random** – Get random movie data.

## Request and Response Format

### Example Request
```
GET https://moviesdatabase.p.rapidapi.com/titles
Headers:
  X-RapidAPI-Key: your_api_key
  X-RapidAPI-Host: moviesdatabase.p.rapidapi.com
```

### Example Response (JSON)
```json
{
  "results": [
    {
      "id": "tt1375666",
      "titleText": { "text": "Inception" },
      "releaseYear": { "year": 2010 },
      "primaryImage": {
        "url": "https://example.com/inception.jpg"
      }
    }
  ],
  "page": 1,
  "next": "page=2"
}
```

### Notes
- Responses are typically returned in **JSON** format.
- Pagination is enabled through `page` and `next` keys.

## Authentication
To authenticate requests:

- You must include your **RapidAPI Key** in the headers.
- Required headers:
```
X-RapidAPI-Key: YOUR_API_KEY
X-RapidAPI-Host: moviesdatabase.p.rapidapi.com
```
Without these headers, the API will reject the request.

## Error Handling
Common error responses include:

- **400 Bad Request** – Missing or invalid query parameters.
- **401 Unauthorized** – Invalid or missing API key.
- **404 Not Found** – Resource does not exist (e.g., invalid movie ID).
- **429 Too Many Requests** – Rate limit exceeded.
- **500 Internal Server Error** – Server issue on API provider's side.

### How to Handle Errors in Code
- Always wrap API calls in `try/catch`.
- Validate user input before sending requests.
- Implement retry logic for **429** errors.
- Log error messages for debugging.

## Usage Limits and Best Practices
- The API may enforce **rate limits** (e.g., requests per minute).
- Avoid unnecessary repeated requests—use caching.
- Fetch only the data you need using query parameters.
- Handle pagination when retrieving large datasets.
- Keep your API key secure and avoid exposing it in frontend code.

