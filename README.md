# Iyzico API Client Library

## Introduction

This project is an API client library for Iyzico, generated using OpenAPI. It provides a TypeScript Axios client for interacting with the Iyzico API.

## Installation

To set up the project, follow these steps:

1. Clone the repository:
   ```sh
   git clone https://github.com/centrual/iyzico-iyzipay.git
   cd iyzico-iyzipay
   ```

2. Install dependencies:
   ```sh
   yarn install
   ```

3. Ensure you are using Node.js version 22. You can use any Node.js version manager like nvm or volta.sh.

## Usage

To generate and build the API client library, follow these steps:

1. Install the OpenAPI Generator CLI globally:
   ```sh
   yarn global add @openapitools/openapi-generator-cli
   ```

2. Generate the TypeScript Axios client library from the OpenAPI specification:
   ```sh
   openapi-generator-cli generate -i ./Iyzico-API.yaml -g typescript-axios -c ./generator_configs/node_api_client.config.json -o ./node_api_client
   ```

3. Navigate to the generated directory and install dependencies:
   ```sh
   cd ./node_api_client
   yarn install
   ```

4. Build the package:
   ```sh
   yarn build
   ```

### Importing the Package

To use the generated client library, import it into your project. Note that the API class names are generated based on the tags in the OpenAPI specification.

```typescript
import { Configuration, PaymentApi } from 'iyzico-iyzipay';
```

### Setting Up the API Client

Set up the API client with your API key:

```typescript
const config = new Configuration({ apiKey: 'YOUR_API_KEY' });
const paymentApi = new PaymentApi(config);
```

### Adding an Interceptor

You can add an interceptor to log or modify requests:

```typescript
import axios from 'axios';

axios.interceptors.request.use(request => {
  console.log('Starting Request', request);
  return request;
});

axios.interceptors.response.use(response => {
  console.log('Response:', response);
  return response;
});
```

## Configuration

The project uses a configuration file (`generator_configs/node_api_client.config.json`) for the OpenAPI generator. The configuration includes settings such as:

- `supportsES6`: Enables ES6 support.
- `enumPropertyNaming`: Sets the naming convention for enum properties.
- `prependFormOrBodyParameters`: Prepends form or body parameters.
- `withInterfaces`: Generates interfaces.
- `withSeparateModelsAndApi`: Separates models and API.
- `apiPackage`: Specifies the API package name.
- `modelPackage`: Specifies the model package name.
- `npmName`: Sets the npm package name.
- `npmRepository`: Sets the npm repository URL.
- `npmVersion`: Sets the npm package version.
- `withoutPrefixEnums`: Removes prefix from enums.
- `gitHost`: Sets the Git host.
- `gitUserId`: Sets the Git user ID.
- `gitRepoId`: Sets the Git repository ID.

## Contributing

We welcome contributions! Please follow these steps to contribute:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes.
4. Commit your changes (`git commit -m 'Add new feature'`).
5. Push to the branch (`git push origin feature-branch`).
6. Create a new Pull Request.

## License

This project is licensed under the MIT License.