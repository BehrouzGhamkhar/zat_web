---
title: "Installation"
weight: 1
---

# Installation

## Prerequisites

Before installing the Session Manager UI, make sure the following are available on your machine.

### System Requirements

| Requirement | Minimum Version | Notes |
|---|---|---|
| Node.js | v18.0.0 | LTS version recommended |
| npm | v9.0.0 | Comes bundled with Node.js |
| Git | any recent version | For cloning the repository |
| A modern browser | Chrome  / Firefox | Required for Plotly rendering |

> **Tip:** You can check your installed versions by running `node -v` and `npm -v` in a terminal.

### Backend Server

The UI communicates with a backend server for all sensor data and recording controls. Make sure the backend is running and reachable before starting the UI. See the backend repository documentation for setup instructions.

<!-- TODO: link to backend repository docs -->

---

## Installing the UI

### 1. Clone the Repository

```bash
git clone <YOUR_REPO_URL>
cd <YOUR_REPO_FOLDER>
```

<!-- TODO: replace with actual repo URL -->

### 2. Install Dependencies

```bash
npm install
```

This will install all required packages, including React, Plotly, and routing libraries.

### 3. Configure the Backend URL

The UI reads the backend server address from a configuration file located at:

```
src/configs/config.js
```

Open this file and set `BASE_URL` to point to your running backend instance:

```js
export const SERVER_CONFIG = {
  BASE_URL: "http://<YOUR_BACKEND_HOST>:<PORT>"
};
```

For example, if your backend runs locally on port `8000`:

```js
export const SERVER_CONFIG = {
  BASE_URL: "http://localhost:8000"
};
```

> **Note:** If you are running the UI and backend on different machines, use the backend machine's IP address instead of `localhost`.

---

## Running the Application

Start the development server:

```bash
npm start
```

The app will be available at [http://localhost:3000](http://localhost:3000) by default. It will automatically reload when you make changes to source files.

### Building for Production

To create an optimised production build:

```bash
npm run build
```

The output will be placed in the `build/` directory and can be served with any static file server.

---

## Verifying the Setup

Once the app is running, open it in your browser. You should see the Session Manager home screen:

{{< hint info >}}
📸 **Screenshot placeholder** — *Home screen on first load*
{{< /hint >}}

If the UI loads but sensor panels show no data, check that:

1. The backend server is running.
2. The `BASE_URL` in `config.js` is correct.
3. Your browser console (F12 → Console) shows no network errors.

---

## Troubleshooting

**`npm install` fails with peer dependency errors**
Try running with the legacy peer deps flag:
```bash
npm install --legacy-peer-deps
```

**Sensor data does not appear**
Open the browser developer console and look for failed network requests. The UI polls the backend every 500 ms; a connection error will be logged there.

**Blank page after `npm start`**
Ensure you are using a supported Node.js version. Run `node -v` and compare against the table above.
