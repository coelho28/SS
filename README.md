# Project: OAuth Server Implementation

## Overview

This project consists of two main components: an OAuth server and a client application. 
The OAuth server handles user authentication and authorization providing tokens to the client app, while the client application interacts with the server to authenticate users and access protected resources.

## Components

### 1. OAuth Server

The OAuth server is responsible for managing user registration, login, and token issuance. It provides endpoints for user interaction and authentication.

#### Key Features

- **User Registration**: Allows users to register via a web interface.
- **User Login**: Facilitates user login through a web interface.
- **Auth Code Issuance**: Issues tokens for authorization codes, to be later used to issue access tokens.
- **Token Issuance**: Issues tokens for authenticated users.

## Installation

### 1. Clone repository
### 2. Navigate to Project directoy
### 3. Install dependencies

npm install

### 4. Start Client App

npm start

### 5. Start AuthServer

node src/oauth2.js

## Usage

Access the OAuth server at http://localhost:8000
Access the client application at http://localhost:3000

The following uris are implemented in the client app:
- **/auth/register**: Redirects the users to the OAuth server to do the registation.
- **/auth/login**: Redirects the users to the OAuth server to do the login.
- **/done**: To confirm that the user is accessing the resource with the expected access token.
- **/auth/provider/failure**: In case that the authorization fails.
- **/auth/provider**: Redirects to the OAuth server to issue the authotization code, to later on be user to issue the access token. For this one, it's necessary to have an Authotization Bearer Header, with the JWT provided, by the OAuth Server, after the login.
- **/auth/provider/callback**: Redirects to the OAuth server, after issuing the authcode, to issue the access token.

The following uris are implemented in the oauth server:
- **/register**: Which is providing an interface to input the user credentials.
- **/login**: Which is providing an interface to input the user credentials, and responding with a JWT which can be then used to issue the authcode.
- **/authorize**: Verifies the user JWT and client app, and retrieves an authcode.
- **/token**: Validates the client app and authcode, and retrieves an JWT for the access token.
