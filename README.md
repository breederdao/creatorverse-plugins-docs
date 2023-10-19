# Creatorverse Plugins Docs

## Base API Reference

**Base URL**
http://bdao-ecs-crtrvrs-wallet-api-dev-2122478437.ap-southeast-1.elb.amazonaws.com/api/v1

**Output Pin Structure for All Blueprints:**

- **OnSuccess:** Triggered upon a successful API request.
- **OnFail**: Triggered if an error occurs during the API request.
- **Data:** Holds data from a successful API request (only available when OnSuccess is activated).
- **Message:** Contains error message for a failed API request (populated when OnFail is triggered).
- **Response Code:** Indicates the HTTP response code received.


## Installation

1. Request CreatorVerse UE plugins from the BreederDAO team.
2. Navigate to your root project directory. Create a new folder named Plugins and add the received plugins to this folder.
3. Open the Unreal Engine editor. You will be prompted to compile the plugin. Follow the on-screen instructions to complete the compilation process.

- Search for the BreederDAO subsystem.

<img width="600" alt="Screenshot 2023-09-27 at 1 13 36 PM" src="./assets/blueprints/0_subsystem.png">

## BreederDAO Blueprints


### Registration

**Description:**

Enables users to create a Creatorverse account.

[API Reference:](http://bdao-ecs-crtrvrs-wallet-api-dev-2122478437.ap-southeast-1.elb.amazonaws.com/api/v1#/user/UserController_register)


<img width="600" alt="Registration" src="./assets/blueprints/1_registration.png">

**Input Pin:**

- Username
- Email
- Password
- Confirm Password

**Email Verification:**

Upon registration, users receive a verification email to confirm the validity of their email address.

### Login

**Description:**

Facilitates user login to the Creatorverse game.

**Pre-requisite:**

- User must be registered.

[API Reference:](http://bdao-ecs-crtrvrs-wallet-api-dev-2122478437.ap-southeast-1.elb.amazonaws.com/api/v1#/auth/AuthController_login)

<img width="600" alt="Login" src="./assets/blueprints/2_login.png">

**Input Pin:**

- Email or Username
- Password

**Data Struct:**

<img width="500" alt="Login Struct" src="./assets/blueprints/2_login_data.png">

**Note:** Upon successful login, a Bearer token will be generated. This token is essential for accessing other APIs within the Creatorverse ecosystem.

### Get User Data

**Description:**

Retrieve user account data, including user information, DATs, and currency balances.

**Pre-requisite:**

- User must be logged in.

[API Reference:](http://bdao-ecs-crtrvrs-wallet-api-dev-2122478437.ap-southeast-1.elb.amazonaws.com/api/v1#/user/UserController_getUser)

<img width="600" alt="Login" src="./assets/blueprints/3_getUserData.png">

**Data Struct:**

<img width="600" alt="Login" src="./assets/blueprints/3_getUserdData_data.png">

### Get User Dats

**Description:**

Fetch the current user’s DATs.

[API Reference:](http://bdao-ecs-crtrvrs-wallet-api-dev-2122478437.ap-southeast-1.elb.amazonaws.com/api/v1#/user/UserController_getUserDats)

<img width="600" alt="Login" src="./assets/blueprints/4_getUserDats.png">

**Data Struct:**

<img width="600" alt="Login" src="./assets/blueprints/4_getUserDats_data.png">

### Get User Currencies Balance

**Description:**

Retrieve the current user’s currency balances.

[API Reference:](http://bdao-ecs-crtrvrs-wallet-api-dev-2122478437.ap-southeast-1.elb.amazonaws.com/api/v1#/user/UserController_getUserCurrencies)

<img width="600" alt="Login" src="./assets/blueprints/5_getUserCurrencies.png">

**Data Struct:**

<img width="699" alt="Login" src="./assets/blueprints/5_getUserCurrencies_data.png">

### Get All DATS

**Description:**

Access a complete list of playable DATs in the game.

[API Reference:](http://bdao-ecs-crtrvrs-wallet-api-dev-2122478437.ap-southeast-1.elb.amazonaws.com/api/v1#/dats/DatController_getDats)

<img width="600" alt="Login" src="./assets/blueprints/8_getAllDATs.png">

**Data Struct:**

<img width="600" alt="Login" src="./assets/blueprints/4_getUserDats_data.png">

### Add User DAT

**Description:**

Associate specific DATs with a player's account. Obtain UserId by calling the [Get User Data](https://github.com/breederdao/creatorverse-plugins-docs/#get-user-data) plugin.

**Input Pin:**

- UserId
- Dat Enum

<img width="300" alt="Add User DAT Enum" src="./assets/blueprints/6_addUserDat_enum.png">

[API Reference:](http://bdao-ecs-crtrvrs-wallet-api-dev-2122478437.ap-southeast-1.elb.amazonaws.com/api/v1#/user/UserController_updateUserDat)

<img width="600" alt="Add User DAT" src="./assets/blueprints/6_addUserDat.png">

**Data Struct:**

<img width="600" alt="Add User DAT Data" src="./assets/blueprints/6_addUserDat_data.png">

### Update User Currency Balance

**Description:**

Modify a player's currency balance. Use -1 for Gems, Relics Fragments, and Cores to retain the current balance. UserId can be obtained through the [Get User Data](https://github.com/breederdao/creatorverse-plugins-docs/#get-user-data) plugin

**Input Pin:**

- Gems
- Relics Fragments
- Cores

[API Reference:](http://bdao-ecs-crtrvrs-wallet-api-dev-2122478437.ap-southeast-1.elb.amazonaws.com/api/v1#/user/UserController_updateUserCurrencies)

<img width="600" alt="Add User DAT" src="./assets/blueprints/7_updateCurrencyBalance.png">

**Data Struct:**

<img width="600" alt="Add User DAT Data" src="./assets/blueprints/5_getUserCurrencies_data.png">



