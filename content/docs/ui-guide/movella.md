---
title: "Movella Sensors"
weight: 2
---

# Movella Sensors

The Movella Sensors page displays live orientation and motion data streamed from up to **five Movella IMU sensors** simultaneously. Data is fetched from the backend every 500 ms and plotted in real time.

{{< hint info >}}
 *Screenshot placeholder — Movella Sensors page with all panels expanded and data streaming
{{< /hint >}}

---

## Layout

The page is divided into **collapsible graph panels** stacked vertically, followed by a **sensor toggle bar** at the bottom.

Each panel can be expanded or collapsed individually by clicking its header. This is useful for focusing on a specific data type when your screen space is limited.

---

## Graph Panels

### Roll

Displays the roll angle (rotation around the X axis) in degrees for each active sensor over time.

{{< hint info >}}
 Screenshot placeholder — Roll panel expanded, showing live lines for multiple sensors
{{< /hint >}}

### Pitch

Displays the pitch angle (rotation around the Y axis) in degrees.

{{< hint info >}}
 Screenshot placeholder — Pitch panel
{{< /hint >}}

### Yaw

Displays the yaw angle (rotation around the Z axis) in degrees.

{{< hint info >}}
 Screenshot placeholder — Yaw panel
{{< /hint >}}

> All three Euler angle panels share the same Y-axis label: Angle (degree). The X axis shows wall-clock time formatted as `HH:MM:SS`.

### Quaternions

Displays all four quaternion components — X, Y, Z, W — for each active sensor on a single graph. Each component is drawn as a separate line.

{{< hint info >}}
 Screenshot placeholder — Quaternions panel with four lines per sensor visible
{{< /hint >}}

> Quaternion values are dimensionless and range from −1 to +1.

### Accelerometer

Displays the linear acceleration along X, Y, and Z axes. Y-axis label: Acceleration

{{< hint info >}}
 Screenshot placeholder — Accelerometer panel
{{< /hint >}}

### Gyroscope

Displays the angular velocity around X, Y, and Z axes. Y-axis label: Angular Velocity.

{{< hint info >}}
 Screenshot placeholder — Gyroscope panel
{{< /hint >}}

### Magnetometer

Displays the magnetic field strength along X, Y, and Z axes. Y-axis label: Magnetic Field.

{{< hint info >}}
 Screenshot placeholder — Magnetometer panel
{{< /hint >}}

---

## Collapsing and Expanding Panels

Click anywhere on a panel header to toggle it open or closed. An arrow indicator shows the current state:

- Panel is expanded (data graph visible)
- Panel is collapsed (hidden to save space)

All panels start expanded by default when the page loads.

---

## Sensor Toggle Bar

At the bottom of the page is a row of checkboxes — one per sensor. Use these to show or hide individual sensors across all graphs simultaneously.

{{< hint info >}} Screenshot placeholder — Sensor toggle bar with some sensors unchecked
{{< /hint >}}

| Control                   | Effect |
|---------------------------|---|
| Checkbox <b>checked</b>   | Sensor's data lines are visible in all graphs |
| Checkbox <b>unchecked</b> | Sensor is hidden from all graphs (data is still collected in the background) |

This is particularly useful when one sensor is noisy or not yet attached — you can hide it without stopping the stream.

---

## Data Behaviour

- The graph displays the <last 50 data points per sensor (sliding window). Older points scroll off the left edge as new ones arrive.
- Timestamps are deduplicated — if a polling response contains data that has already been plotted, it is silently skipped.
- Sensors are <b>dynamically discovered</b> on page load. If no sensors are connected, the toggle bar and graphs will be empty.

---

## Troubleshooting

<b>Graphs are empty / no lines appear</b>

- Confirm the backend is running and the Movella sensors are publishing data.
- Check that the relevant sensor checkboxes at the bottom are ticked.
- Open the browser console (F12) and look for fetch errors targeting `/movella/data`.

<b>One sensor is missing from the toggle bar</b>
- That sensor's ID was not present in the initial backend response. Verify the sensor is connected and the backend recognises it, then refresh the page.
