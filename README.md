# MoviesDatabase API Documentation

## Overview

The MoviesDatabase API provides comprehensive access to movie-related data, including movies, TV shows, and actor information. This API enables developers to build rich applications with features like search functionality, detailed content retrieval, and access to trending media content.

### Key Features

- Detailed information about movies, TV shows, and actors
- Image assets (posters, backdrops, actor photos)
- Real-time trending and popular content
- Multi-language and region support
- Search capabilities across all content types

## API Information

- **Current Version**: 3.0
- **Base URL**: `https://api.themoviedb.org/3`

## Endpoints

### Core Endpoints

| Endpoint | Description |
|----------|-------------|
| `/movie/{id}` | Get detailed movie information |
| `/tv/{id}` | Get detailed TV show information |
| `/trending/all/day` | Get trending movies and TV shows |
| `/search/movie` | Search movies by title, year, etc. |
| `/search/person` | Search actors and crew members |
| `/genre/movie/list` | Get available movie genres |
| `/configuration` | Get API configuration settings |

## Authentication

### API Key Authentication

All requests require an API key from The Movie Database (TMDb). You can include it in either of these ways:

```bash
# As a query parameter
GET https://api.themoviedb.org/3/movie/{movie_id}?api_key=your_api_key

# As a bearer token
Authorization: Bearer your_api_key
```

## Request & Response Format

### Example Request

```bash
GET https://api.themoviedb.org/3/movie/550?api_key=your_api_key
```

### Example Response

```json
{
  "id": 550,
  "title": "Fight Club",
  "overview": "A man finds himself growing increasingly frustrated with his life and creates an underground fight club.",
  "release_date": "1999-10-15",
  "genres": [
    { "id": 18, "name": "Drama" },
    { "id": 53, "name": "Thriller" }
  ],
  "poster_path": "/8tVg1YmhtARoiu7ZJZdzQd9PZ8p.jpg"
}
```

## Error Handling

### Status Codes

| Code | Description |
|------|-------------|
| 401 | Unauthorized - Invalid or missing API key |
| 404 | Not Found - Resource doesn't exist |
| 500 | Internal Server Error |

### Error Handling Example

```javascript
fetch('https://api.themoviedb.org/3/movie/{movie_id}?api_key=your_api_key')
  .then(response => {
    if (!response.ok) {
      throw new Error('API error: ' + response.status);
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

## Usage Guidelines

### Rate Limits

- **Free Tier**: 40 requests per second

### Best Practices

1. **Caching**
   - Cache frequently accessed data
   - Implement appropriate cache invalidation strategies

2. **Request Optimization**
   - Always include your API key
   - Avoid excessive requests to search endpoints
   - Use pagination for large result sets

3. **Error Management**
   - Implement proper error handling
   - Provide meaningful error messages to users
   - Include retry logic for failed requests

## Support

For additional support or questions, please refer to the official MoviesDatabase API documentation or contact their support team.

---

*Note: Replace `your_api_key` with your actual API key in all examples.*