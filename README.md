# Kita Navigator Berlin API

**Last Updated:** 08. November 2025

OpenAPI specification for the Kita Navigator Berlin API - a service for searching and finding daycare centers (Kitas) in Berlin.

## Overview

This repository contains the OpenAPI 3.0 specification for the Kita Navigator Berlin API, which provides:

- **Kita Search**: Search for daycare centers by name with pagination
- **Count Results**: Get total number of Kitas matching search criteria
- **Watchlist**: Manage favorite Kitas (requires authentication)

## API Documentation

The complete API specification is available in `openapi.yaml`.

### Base URLs

- **Search API**: `https://kita-navigator.berlin.de/api/v1`
- **Watchlist API**: `https://kita-navigator.berlin.de/merkliste/api/v1` (requires authentication)

### Endpoints

#### Public Endpoints (No Authentication Required)

- `GET /kitas/namensucheAnzahl` - Get count of Kitas matching search criteria
- `GET /kitas/namensuche` - Search for Kitas with pagination

#### Authenticated Endpoints

- `GET /merklisteneintraege/filter` - Get watchlist entries by IDs (requires session cookies)

## Example Usage

### Search for all Kitas (first page)

```bash
curl 'https://kita-navigator.berlin.de/api/v1/kitas/namensuche?betb=10-2025&einfacheSuche=false&name=*&seite=0&max=12'
```

### Get total count of Kitas

```bash
curl 'https://kita-navigator.berlin.de/api/v1/kitas/namensucheAnzahl?einfacheSuche=false&name=*'
```

## Response Data

Each Kita includes:

- Basic information (ID, name, registration number)
- Address details (street, postal code, city)
- Geographic coordinates (longitude, latitude)
- Availability status for upcoming months
- Preview image URL

## Development

### View the API Documentation

You can view the OpenAPI specification using:

- [Swagger Editor](https://editor.swagger.io/) - paste the `openapi.yaml` content
- [Swagger UI](https://swagger.io/tools/swagger-ui/)
- [Postman](https://www.postman.com/) - import the OpenAPI file

### Generate Client Code

Use [OpenAPI Generator](https://openapi-generator.tech/) to generate client libraries:

```bash
openapi-generator-cli generate -i openapi.yaml -g python -o ./client/python
openapi-generator-cli generate -i openapi.yaml -g typescript-fetch -o ./client/typescript
```

## Data Structure

- **2,856 Kitas** currently available in the database (as of November 2025)
- **238 pages** with 12 results per page
- **9 months** of availability status per Kita

## License

This is an unofficial API specification for the Kita Navigator Berlin service. The actual API is operated by the City of Berlin.

## Related Links

- [Kita Navigator Berlin](https://kita-navigator.berlin.de/)
- [Berlin Open Data Portal](https://daten.berlin.de/)
