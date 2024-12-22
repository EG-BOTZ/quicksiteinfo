# QuickSiteInfo

**QuickSiteInfo** delivers comprehensive information about any website using just its URL. Validate URLs, retrieve favicons, and extract additional data such as social media links and contact numbers—all in a single API call. Perfect for developers looking to integrate essential website data seamlessly into their applications.

## Table of Contents

- [Features](#features)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
  - [Endpoint: POST /collect](#endpoint-post-collect)
  - [Examples](#examples)
- [Responses](#responses)
  - [Success Response](#success-response)
  - [Error Responses](#error-responses)
- [API Reference](#api-reference)
- [FAQ](#faq)
- [Support](#support)
- [License](#license)

## Features

- **URL Validation:** Ensure that a provided URL is valid and active.
- **Favicon Retrieval:** Obtain the website's favicon for branding purposes.
- **Data Extraction:** Fetch social media links and phone numbers embedded within the site.
- **Efficient & Fast:** Get all necessary information with minimal API calls.
- **Easy Integration:** Simple RESTful API design for effortless implementation.

## Getting Started

### Prerequisites

- **RapidAPI Account:** Sign up for a [RapidAPI](https://rapidapi.com/) account to access **QuickSiteInfo**.
- **API Key:** Obtain your API key from the RapidAPI dashboard after subscribing to **QuickSiteInfo**.

### Installation

No installation is required as **QuickSiteInfo** is accessible via RapidAPI. However, you can use tools like `curl`, Postman, or integrate it into your application using various programming languages.

## Usage

### Endpoint: POST /collect

Collects information about a website based on its URL.

**URL:** `https://quicksiteinfo.p.rapidapi.com/v1/collect`

**Method:** `POST`

**Headers:**

- `Content-Type: application/json`
- `X-RapidAPI-Key: YOUR_RAPIDAPI_KEY`
- `X-RapidAPI-Host: quicksiteinfo.p.rapidapi.com`

**Request Body:**

```json
{
  "url": "https://www.example.com/"
}
```

### Examples

#### Example 1: Using `curl`

```bash
curl -X POST 'https://quicksiteinfo.p.rapidapi.com/v1/collect' \
-H 'Content-Type: application/json' \
-H 'X-RapidAPI-Key: YOUR_RAPIDAPI_KEY' \
-H 'X-RapidAPI-Host: quicksiteinfo.p.rapidapi.com' \
-d '{"url": "https://www.example.com/"}'
```

#### Example 2: Using JavaScript (`fetch`)

```javascript
const fetch = require('node-fetch');

const options = {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'X-RapidAPI-Key': 'YOUR_RAPIDAPI_KEY',
    'X-RapidAPI-Host': 'quicksiteinfo.p.rapidapi.com'
  },
  body: JSON.stringify({ url: 'https://www.example.com/' })
};

fetch('https://quicksiteinfo.p.rapidapi.com/v1/collect', options)
  .then(response =&gt; response.json())
  .then(response =&gt; console.log(response))
  .catch(err =&gt; console.error(err));
```

#### Example 3: Using Python (`requests`)

```python
import requests

url = "https://quicksiteinfo.p.rapidapi.com/v1/collect"

payload = {"url": "https://www.example.com/"}
headers = {
    "Content-Type": "application/json",
    "X-RapidAPI-Key": "YOUR_RAPIDAPI_KEY",
    "X-RapidAPI-Host": "quicksiteinfo.p.rapidapi.com"
}

response = requests.post(url, json=payload, headers=headers)

print(response.json())
```

## Responses

### Success Response

**Status Code:** `200 OK`

**Body:**

```json
{
  "validDomain": true,
  "mainLink": "https://www.example.com/",
  "favicon": "https://www.example.com/favicon.ico",
  "faviconBase64": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...",
  "socialLinks": {
    "linkedin": "https://www.linkedin.com/company/example",
    "instagram": "https://www.instagram.com/example",
    "twitter": "https://twitter.com/example",
    "facebook": "https://www.facebook.com/example"
  },
  "phones": ["+55 11 99999-9999"],
  "lastScraped": "2024-12-22T16:23:49Z"
}
```

### Error Responses

- **400 Bad Request:** Invalid or missing URL.

  **Status Code:** `400 Bad Request`

  **Body:**

  ```json
  {
    "error": "Invalid or missing URL."
  }
  ```

- **500 Internal Server Error:** Server encountered an unexpected condition.

  **Status Code:** `500 Internal Server Error`

  **Body:**

  ```json
  {
    "error": "Internal server error."
  }
  ```

## API Reference

Refer to the complete [OpenAPI Specification](./openapi.yaml) for detailed information about all available endpoints, request bodies, and response formats.

## FAQ

### 1. How do I get started with QuickSiteInfo?

- **Sign Up:** Create an account on [RapidAPI](https://rapidapi.com/).
- **Subscribe:** Navigate to **QuickSiteInfo** and subscribe to the desired pricing plan.
- **Obtain API Key:** After subscribing, retrieve your API key from the RapidAPI dashboard.
- **Make Requests:** Use the provided endpoints with your API key to start fetching website information.

### 2. What does QuickSiteInfo do?

QuickSiteInfo validates URLs, retrieves the website's favicon, and extracts additional data such as social media links and phone numbers from the provided website URL.

### 3. What are the pricing plans?

QuickSiteInfo offers multiple pricing tiers, including a free plan with limited requests and paid plans with higher or unlimited request quotas. Visit the [pricing section](#pricing) on RapidAPI for detailed information.

### 4. How accurate is the data extracted by QuickSiteInfo?

QuickSiteInfo uses reliable methods and tools to ensure the accuracy of the extracted data. However, the accuracy depends on how the target website structures its data.

### 5. Can I use QuickSiteInfo for any website?

QuickSiteInfo is designed to work with any publicly accessible website. However, some websites with complex structures or heavy use of JavaScript may yield limited results.

## Support

If you encounter any issues or have questions, feel free to reach out:

- **GitHub Issues:** [GitHub Repository](https://github.com/EG-BOTZ/quicksiteinfo/issues)

## License

This project is licensed under the [MIT License](LICENSE).
