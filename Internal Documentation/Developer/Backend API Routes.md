---
layout: page
title: Backend API Routes
permalink: /internal/dev/backend-api
parent: Developers
grand_parent: Internal Documentation
---

# Backend API Routes

The server's API endpoints are defined under `server/routes/api_v1/`. The files here recieve requests from the client, query or modify the database or filesystem resource, and return a formatted response to the client. The response format and a list of these endpoints exists in the [README](https://github.com/Plea-Justice/researcher-console#server-api-v1). Read these files for the JSON `result` the client can expect to recieve.

| File | Description |
|-|-|
|index.js| Delegates API routes to other files. |
|auth.js| Handles user authentication and registration. |
|scenario.js| Handles scenario save and management. |
|assets.js| Handles asset uploads and management. |
|sim-generate.js| Handles simulation generation and packaging. |
|admin.js| Handles administrator-only operations. |

## Authentication

On any request to the server, [`express-session`](https://www.npmjs.com/package/express-session) automatically attaches a cookie containing a session id. It records that id in the `sessions` collection of the [database](/internal/dev/backend-data) which is later used to track the logged-in state of that session.

The middleware functions in `server/middleware/authenticateRoutes.js` are loaded on most routes and prevent requests from sessions that are not logged-in or that for which the user does not have appropriate permissions. Once a user is logged-in, the permitted API endpoints become accessible.

A user begins authentication by calling `POST /api/v1/auth/login`. This triggers a lookup of the user in the `users` collection of the database. If a match is found, the bcrypt-hashed password is compared with that of the database. On success, the server marks the user's session as logged-in with the requested username. Subsequent requests to `GET /api/v1/auth/user` will return the user and its permissions list. The user can then access authenicated routes.

If a user does not yet have an account, they may first create one with `POST /api/v1/auth/register`. This enters the new username and hashed password into the database and creates the user's assets directory.

The session can be ended with `POST /api/v1/auth/logout`, which destroys the record of the session.

Authentication endpoints are rate-limited using [`express-rate-limit`](https://www.npmjs.com/package/express-rate-limit).

Relevant Files:

- `server/routes/api_v1/auth.js`
- `server/models/UserModel.js`
- `server/middleware/authenticateRoutes.js`
- `server/middleware/userSessionCount.js`

## Scenario Management

Scenarios are represented as a flattened version of the client state with additional properties stored in the `scenarios` collection of the database. They are retrieved by the `user_id` property which is the object ID of the user they they are associated with. Some methods, such as `GET /api/v1/scenarios`, return only a subset of the scenario object which is equivalent to the information stored in `meta` of the client state.

Relevant Files:

- `server/routes/api_v1/scenario.js`
- `server/models/ScenarioModel.js`

## Asset Management

Users may manage assets in their own user data directory. This directory is created when the user registers their account and includes a copy of the default asset library.

Asset uploads are handled by [`express-fileupload`](https://www.npmjs.com/package/express-fileupload) which automatically recieves uploaded files and makes them available as part of the request object. Several checks are performed to make sure the asset type matches its extension, and the filename string is sanitized with [`sanitize-filename`](https://www.npmjs.com/package/sanitize-filename) before it is saved.

Clip and actor (`JavaScript`) assets may not be renamed due to implementation issues with Animate. These assets are also run through a script which [enables asset customization](/internal/dev/asset-customization).

Finally, a new process is started to generate a thumbnail of each asset in the background. Because the Animate assets use the HTML canvas and other browser JavaScript unavailable in Node, [`puppeteer`](https://www.npmjs.com/package/puppeteer) is used to render thumbnails in a headless Chromium instance.

Relevant Files:

- `server/routes/api_v1/assets.js`
- `server/common/thumbnail.js`

## Simulation Interoperability

Relevant Files:

- `server/routes/api_v1/sim-generate.js`
- `server/common/publish.js`

## Administration

These endpoints include middleware which require administrator permissions and the user's password to access.

An administrator may list and modify the properties of all users. Additionally they may change the password of a user and delete a user. On user deletion, their database record and assets directory are destroyed.

Relevant Files:

- `server/routes/api_v1/admin.js`
- `server/models/UserModel.js`
- `server/middleware/authenticateRoutes.js`
