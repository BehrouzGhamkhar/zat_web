---
title: "Quick Start"
weight: 2
---

# Quick Start

This page gives you a fast walkthrough of a typical session — from launching the app to saving recorded data.

## Step 1 — Start the Backend

Make sure your backend server is running before opening the UI. All sensor data and recording commands flow through it.

```bash
# Example — replace with your actual backend start command
ros2 launch session_manager session_manager.launch.py
```

<!-- TODO: replace with actual backend launch command -->

## Step 2 — Launch the UI

```bash
npm start
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

{{< figure src="/images/HomeScreen.jpg" alt="Home Screen" >}}


## Step 3 — Check Your Sensors

Use the side panel to navigate to each sensor view and confirm live data is streaming:

- **Movella** — Roll, Pitch, Yaw graphs should be updating
- **EmotiBit** — PPG, EDA, and other streams should appear
- **eSense** — Temperature graph should be updating

If a graph is empty, the corresponding sensor may not be connected or publishing data yet.

## Step 4 — Configure Topics to Record

Navigate to **Saver Panel** from the side menu.

1. The panel will list all available ROS topics and their active status.
2. Check the topics you want to record. Leave all boxes unchecked to record **everything**.
3. Click **Send** to apply your selection.

{{< figure src="/images/SaverPanel.jpg" alt="Saver Panel" >}}


## Step 5 — Start Recording

Click the green **START** button in the Saver Panel. The LED indicator next to the heading will turn green to confirm recording is active.

{{< hint warning >}}
⚠️ Always confirm the LED indicator is green before beginning an experiment session.
{{< /hint >}}

## Step 6 — Stop Recording

Click the red **STOP** button when your session is complete. The status message below the buttons will confirm the recording has stopped.

---

## What's Next?

- Read the full [UI Guide]({{< relref "/docs/ui-guide" >}}) for a detailed breakdown of every panel.
- Learn about [Movella Sensors]({{< relref "/docs/ui-guide/movella" >}}) and how to toggle individual sensors.
- Learn about [EmotiBit]({{< relref "/docs/ui-guide/emotibit" >}}) stream configuration.
