# Backend Service README

This repository contains a Node.js application that serves as a backend service. The purpose of this service is to interact with both AWS IoT and Firebase services, providing an interface for managing and retrieving information related to devices.

## Prerequisites

Before running the application, ensure you have the following prerequisites installed:

- [Node.js](https://nodejs.org/)
- [npm](https://www.npmjs.com/) (Node Package Manager)

## Getting Started

1. Clone this repository to your local machine:

    ```bash
    git clone *ENTER REPO URL HERE*
    ```

2. Install the project dependencies:

    ```bash
    cd *ENTER REPO NAME HERE*
    npm install
    ```

3. Set up AWS IoT and Firebase:

    - Obtain AWS IoT credentials and update the following files in the `certs` directory:
        - `aws_private.pem.key`
        - `backend_device_certificate.pem.crt`
        - `AmazonRootCA1.pem`
        
    - Obtain Firebase credentials and update the `certs/hiro-v1-firebase-adminsdk-n9cku-9c56012404.json` file.


3. Run the application:

    ```bash
    npm run dev
    ```

    The server will start and be accessible at `http://localhost:8080`.

## API Endpoints

### POST /api

Send data to AWS IoT and update Firebase Firestore with device information.

#### Request Body

```json
{
  "uid": "user-uid",
  "topic": "iot-topic",
  "data": {
    "deviceId": "device-id",
    // Additional data fields
  }
}
```

#### Response

- `200 OK`: Successful request. Returns success message.
- `401 Unauthorized`: Invalid token or missing parameters.

## Token Validation

Token validation is performed using Firebase Firestore. The `checkCred` function checks the validity of the provided token by querying the Firestore collection for the user's information.

## Contributing

If you find any issues or have suggestions for improvement, feel free to open an issue or create a pull request.

## License

This project is licensed under the [MIT License](LICENSE).