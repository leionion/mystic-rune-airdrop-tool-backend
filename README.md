---

# Mystic Runestone Airdrop Tool Backend

## Overview

The Runestone Airdrop Backend is a server application that facilitates the airdrop of Runestone tokens. The backend is developed using Node.js and Express.js and includes API endpoints for various functionalities such as redeeming fees, estimating transaction fees, and managing different amounts for airdrops. The project also integrates Swagger UI for API documentation.

## Project Structure

```
root/
├── config/
│   └── config.ts
├── routes
│   └── AirdropRoute
│        ├── different-amount.route.ts
│        ├── large-different-amount.route.ts
│        ├── large-different-amount-airdrop.route.ts
│        ├── same-amount.route.ts
│   └── EstimateRoute
│        ├── different-amount-estimate.route.ts
│        ├── same-amount-estimate.route.ts
│   └── SubRoute
│        └── runestone-fee.route.ts
├── service/
│   └── psbt/
│       ├── CreateAirdropRunestonePsbt.ts
│       ├── redeemRunestoneAmountRunestone.ts
│       ├── redeemRunestoneSameAmount.ts
│       ├── RuneOne.ts
│       ├── RuneSub.ts
│       └── SameAmountEstimate.ts
├── test/
│   ├── CreateTest.ts
│   ├── freeTierAirdrop.ts
│   ├── matchTests.ts
│   └── MWtests.ts
├── utils/
│   ├── blockcypher.api.ts
│   ├── mempool.api.ts
│   ├── TS
│   │   ├── mw.ts
│   │   └── TsUtils.ts
│   └── unisat.api.ts
├── .env.example
├── package.json
├── README.md
├── swagger.yaml
├── tsconfig.json
└── yarn.lock
env
```

## Installation

1. Clone the repository:

   ```
   git clone https://github.com/leionion/rune-airdrop-backend.git
   cd rune-airdrop-backend
   ```

2. Install dependencies:

   ```
   yarn install
   ```

3. Create a `.env` file:

   ```
   cp .env.example .env
   ```

4. Configure the environment variables in `.env` file:
   ```
   PORT=your-port
   ```

## Usage

1. Start the server:

   ```
   yarn dev
   ```

2. The server should be running on the specified port. You can visit `http://localhost:[PORT]` to check if the server is up and running.

3. Access the API documentation via Swagger UI at `http://localhost:[PORT]/api-docs`.

## API Endpoints

Here are some key API endpoints provided by the backend:

- **GET /**: Check if the backend server is running.
- **POST /api/redeem-fee**: Redeem Runestone fees.
- **POST /api/same-amount**: Handle airdrops with the same amount.
- **POST /api/different-amount**: Handle airdrops with different amounts.
- **POST /api/large-different-amount**: Handle large different amount airdrops.
- **POST /api/large-different-amount-airdrop**: Handle large airdrop transactions with different amounts.
- **POST /api/estimate/same-amount**: Estimate transaction fee for same amount airdrop.
- **POST /api/estimate/different-amount**: Estimate transaction fee for different amount airdrop.

## Middleware

- **CORS**: Cross-Origin Resource Sharing is enabled using the `cors` package.
- **Body-Parser**: JSON and URL-encoded data parsing with `body-parser` and `express.json`.

## Swagger

Swagger UI is integrated to provide interactive API documentation. The `swagger.yaml` file is required to configure API documentation, which can be accessed at `/api-docs`.

## Mutex

Mutex from `async-mutex` is used for API rate limit protection functionality.

## Global Variables

- `app.locals.walletIndex`: Global iterator for wallet management.
- `app.locals.iterator`: Global iterator for unisat API distribution.

## Swagger Usage

### Base URL

The base URL for the API is:

- Development: `http://localhost:5000/api`
- Production: `https://rune-airdrop-backend.onrender.com/api`

### Endpoints

#### Different Amount Rune Airdrop

- **Description:** Transfer different amounts of Rune tokens to different addresses
- **Endpoint:** `/different-amount`
- **HTTP Method:** POST

#### Large Different Amount Rune Airdrop

- **Description:** Transfer different amounts of Rune tokens to different addresses (for a large number of addresses)
- **Endpoint:** `/large-different-amount`
- **HTTP Method:** POST

#### Large Different Amount Rune Airdrop (Execute)

- **Description:** Execute the large different amount Rune Airdrop with a pre-generated transaction ID
- **Endpoint:** `/large-different-amount-airdrop`
- **HTTP Method:** POST

#### Same Amount Rune Airdrop

- **Description:** Transfer the same amount of Rune tokens to different addresses
- **Endpoint:** `/same-amount`
- **HTTP Method:** POST

#### Calculate Runestone Transaction Fee

- **Description:** Calculate the fee for a runestone transaction
- **Endpoint:** `/runestone-fee`
- **HTTP Method:** GET

#### Estimate Different Amount Rune Airdrop

- **Description:** Estimate the different amount Rune Airdrop
- **Endpoint:** `/estimate/different-amount`
- **HTTP Method:** POST

#### Estimate Same Amount Rune Airdrop

- **Description:** Estimate the same amount Rune Airdrop
- **Endpoint:** `/estimate/same-amount`
- **HTTP Method:** POST

### Error Handling

In case of errors, the API responds with appropriate HTTP status codes along with error messages in the response body.
