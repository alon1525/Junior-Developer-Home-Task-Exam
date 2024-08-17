---

# Assignment, the website is in the about

## Overview

This is a Node.js application using Express for handling API requests. It includes an endpoint for fetching metadata from provided URLs.

## Prerequisites

- Node.js (v14 or later)
- npm or yarn (package managers)

## Setup

1. **Clone the Repository**

   Clone the repository to your local machine:

   ```bash
   git clone https://github.com/your-username/your-repository.git
   cd your-repository
   ```

2. **Install Dependencies**

   Install the required dependencies using npm or yarn:

   ```bash
   npm install
   # or
   yarn install
   ```

3. **Environment Variables**

   Create a `.env` file in the root directory if you have any environment variables. This step may not be necessary for this example but is recommended for handling sensitive data.

   Example `.env` file:
   ```
   PORT=5021
   ```

4. **Update CORS Configuration**

   In `index.js`, update the CORS settings to fit your requirements. By default, the application is configured to allow all origins. If you need to restrict access, modify the `cors` options in your Express app.

   Example:

   ```javascript
   app.use(cors({
     origin: 'https://your-allowed-origin.com',
     methods: 'GET,POST,PUT,DELETE',
     allowedHeaders: 'Content-Type,Authorization',
   }));
   ```

5. **Run the Application**

   Start the application using npm or yarn:

   ```bash
   npm start
   # or
   yarn start
   ```

   The server will run locally on `http://localhost:5021`.

## Endpoints

### `POST /fetch-metadata`

Fetch metadata from a list of URLs.

**Request Body:**

```json
{
  "urls": [
    "https://example.com",
    "https://another-example.com"
  ]
}
```

**Response:**

```json
[
  {
    "url": "https://example.com",
    "title": "Example Domain",
    "description": "This domain is for use in illustrative examples.",
    "image": "https://example.com/image.jpg"
  },
  {
    "url": "https://another-example.com",
    "title": "Another Example",
    "description": "Another example description.",
    "image": "https://another-example.com/image.jpg"
  }
]
```

**Error Response:**

```json
[
  {
    "url": "https://invalid-url",
    "title": "Error",
    "description": "Error fetching metadata",
    "image": "Error"
  }
]
```

### `GET /`

Check if the server is running.

**Response:**

```text
Server is running and CORS is working
```

## Deployment

To deploy this application to Vercel:

1. **Ensure you have a `vercel.json` configuration file in the root directory.**

2. **Install Vercel CLI:**

   ```bash
   npm install -g vercel
   ```

3. **Deploy:**

   ```bash
   vercel
   ```

   Follow the prompts to deploy your application.
