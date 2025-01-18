# Node.js OAuth 2.0 Server

This project is a Node.js microservice that implements an OAuth 2.0 server. It allows clients to authenticate using a consumer key and secret and provides access tokens for accessing protected resources.

## Features

- Implements OAuth 2.0 Authorization Framework.
- Supports:
  - Client Credentials Grant.
  - Token generation and validation.
- Secure storage of client credentials and access tokens.
- Easy-to-configure environment variables.

## Requirements

- Node.js (v16 or higher)
- npm or yarn
- A database for storing client credentials and tokens (e.g., MongoDB, PostgreSQL).

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/devendra-stuff/Pluto-auth-service.git
   cd Pluto-auth-service
   ```

2. Install dependencies:

   ```bash
   npm install
   # or
   yarn install
   ```

3. Set up the environment variables by creating a `.env` file in the root directory. Example:

   ```env
   PORT=3000
   DATABASE_URL=mongodb://localhost:27017/oauth2
   JWT_SECRET=your_jwt_secret
   TOKEN_EXPIRATION=3600 # in seconds
   ```

4. Start the server:

   ```bash
   npm start
   # or
   yarn start
   ```

   The server will start on the specified `PORT` (default: 3000).

## API Endpoints

### 1. `/token`

#### Method: `POST`

#### Description:
Generates an access token for a client.

#### Request Body:

```json
{
  "client_id": "your-client-id",
  "client_secret": "your-client-secret"
}
```

#### Response:

```json
{
  "access_token": "generated-access-token",
  "token_type": "Bearer",
  "expires_in": 3600
}
```

### 2. `/validate`

#### Method: `POST`

#### Description:
Validates an access token.

#### Request Body:

```json
{
  "access_token": "provided-access-token"
}
```

#### Response:

- **Valid Token:**

  ```json
  {
    "valid": true,
    "client_id": "associated-client-id",
    "expires_at": "timestamp"
  }
  ```

- **Invalid Token:**

  ```json
  {
    "valid": false,
    "error": "Token is invalid or expired"
  }
  ```

## Project Structure

```
.
├── src
│   ├── controllers
│   │   └── tokenController.js  # Handles token-related logic
│   ├── models
│   │   └── clientModel.js     # Schema for storing client credentials
│   │   └── tokenModel.js      # Schema for storing access tokens
│   ├── routes
│   │   └── tokenRoutes.js     # Defines API endpoints
│   ├── services
│   │   └── authService.js     # Business logic for OAuth 2.0
│   └── utils
│       └── jwtUtils.js        # Utility for JWT operations
├── .env.example               # Example environment file
├── package.json
└── README.md
```

## Development

1. Run the development server:

   ```bash
   npm run dev
   # or
   yarn dev
   ```

   This will start the server with hot-reloading enabled.

2. Run tests:

   ```bash
   npm test
   # or
   yarn test
   ```

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a feature branch (`git checkout -b feature-name`).
3. Commit your changes (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature-name`).
5. Open a pull request.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Contact

For questions or support, contact [your-email@example.com](mailto:your-email@example.com).

