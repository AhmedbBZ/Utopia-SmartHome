# Smart House Simulation App

## Introduction

This project is a simulation of a "smart house" system developed using **MongoDB**, **Express.js**, and **React.js**. The application enables users to manage smart houses, rooms, and devices, with functionalities to add, update, and retrieve users and houses. It also features authentication and user role management (admin and invited).

## Features

### User Management

- Add new users with default roles.
- Retrieve user details by email and password.
- Update user information, excluding email.
- Check the validity of an email.
- Change user passwords.
- Fetch all houses where a user is either an admin or an invited user.

### House Management

- Add a new house with a default room named "general" and predefined devices:
  - Router
  - Compteur
  - Camera
  - Movement Detector
  - Temperature Sensor
  - Humidity Sensor
- Retrieve all houses or fetch a specific house by ID.
- Update house details by ID.

### Database Models

#### User Model

```json
{
  "name": "string",
  "email": "string (unique, required)",
  "password": "string (required)",
  "image": "string (optional)",
  "admin": ["string"],
  "invited": ["string"]
}
```

#### House Model

```json
{
  "name": "string (required)",
  "rooms": [
    {
      "name": "string (required)",
      "type": "string (required)",
      "devices": [
        {
          "name": "string (required)",
          "type": "string (required)",
          "status": "string (default: 'off')",
          "room-name": "string (required)",
          "settings": "object (dynamic, default: {})"
        }
      ]
    }
  ]
}
```

## Project Structure

```
root
├── controllers
│   ├── userController.js
│   ├── houseController.js
├── models
│   ├── userModel.js
│   ├── houseModel.js
├── routes
│   ├── userRoutes.js
│   ├── houseRoutes.js
├── services
│   ├── userService.js
│   ├── houseService.js
├── app.js
```

## Installation

1. Clone the repository:

2. Install dependencies for both Backend & Frontend:

   ```bash
   npm install
   ```

3. Set up the environment variables in a `.env` file in Backend:

   ```env
   PORT=3000
   MONGO_URI=your_mongodb_connection_string
   ```

4. Start the application:

   ```bash
   in the Backend :npm run dev
  in the Frontend : npm start
   ```

## API Endpoints

### User Endpoints

- **GET /users**: Retrieve all users.
- **POST /users**: Add a new user.
- **POST /users/login**: Retrieve user details by email and password.
- **POST /users/validate-email**: Check the validity of an email.
- **PATCH /users/update-password**: Update user password.
- **GET /users/houses**: Retrieve all houses (admin and invited) for a user.
- **PUT /users**: Update user details by email.

### House Endpoints

- **GET /houses**: Retrieve all houses.
- **POST /houses**: Add a new house.
- **GET /houses/\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*****:id**: Retrieve house details by ID.
- **PUT /houses/\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*****:id**: Update house details by ID.

## Default Devices

Upon creating a house, the following devices are added to the default room "general":

| Device Name                | Type               | Default Status | Settings                      |
| -------------------------- | ------------------ | -------------- | ----------------------------- |
| general-router             | router             | off            | {}                            |
| general-compteur           | compteur           | off            | { total: 0, "this-month": 0 } |
| general-camera             | camera             | off            | {}                            |
| general-movement-detector  | movement-detector  | off            | { movement: false }           |
| general-temperature-sensor | temperature-sensor | off            | { temperature: 0 }            |
| general-humidity-sensor    | humidity-sensor    | off            | { humidity: 0 }               |

## Technologies Used

- **Backend**: Node.js, Express.js
- **Database**: MongoDB
- **Frontend**: React.js
- **ORM**: Mongoose

## Future Enhancements

- User authentication with JWT.
- Real-time updates for device statuses using WebSockets.
- Integration with IoT devices for real-world simulation.
- Enhanced analytics and reporting for energy consumption.

## License

This project is licensed under the MIT License. Feel free to use and modify it as needed.

---

Feel free to contribute to the project or report issues. Happy coding!\
Your Friend Ahmed Bouzid \
ahmedbouzid973@gmail.com

