---
title: "EmotiBit"
weight: 3
---

# EmotiBit

The EmotiBit page displays live biometric data streamed from the **EmotiBit wearable sensor**. The available data streams are discovered automatically from the backend — the UI adapts to whatever the device is currently publishing.

{{< hint info >}}
📸 **Screenshot placeholder** — *EmotiBit page with several stream panels expanded*
{{< /hint >}}

---

## Layout

Like the Movella page, the EmotiBit view consists of **collapsible graph panels** stacked vertically, with a **stream toggle bar** at the bottom.

Each panel corresponds to one sensor stream (e.g. PPG, EDA, Temperature). Panels can be individually expanded or collapsed.

---

## Available Streams

The streams displayed depend on what the EmotiBit device and backend are publishing. Common streams include:

| Stream | Description | Y-axis Unit |
|---|---|---|
| **PPG** | Photoplethysmography — optical heart rate signal | Intensity |
| **EDA** | Electrodermal Activity (skin conductance) | Conductance (μS) |
| **Temperature** | Skin surface temperature | Temperature (°C) |
| **Accelerometer** | Linear acceleration (X, Y, Z) | Acceleration (m/s²) |
| **Gyroscope** | Angular velocity (X, Y, Z) | Angular Velocity (rad/s) |
| **Magnetometer** | Magnetic field strength (X, Y, Z) | Magnetic Field (μT) |

> The list above reflects the known streams. If additional streams appear, they will be displayed with a generic **Value** label on the Y-axis.

### Multi-channel Streams

Some streams carry multiple channels (for example, Accelerometer has X, Y, and Z). Each channel is drawn as a separate coloured line within the same panel.

{{< hint info >}}
📸 **Screenshot placeholder** — *Accelerometer panel showing three coloured lines for X, Y, Z*
{{< /hint >}}

---

## Graph Panels

### Opening and Closing Panels

Click a **panel header** to toggle it:

- expanded (graph visible)  
- collapsed

All panels are expanded by default when the page loads.

{{< hint info >}}
📸 **Screenshot placeholder** — *Two panels: one expanded, one collapsed*
{{< /hint >}}

### Reading the Graphs

- The **X axis** shows wall-clock time (`HH:MM:SS`).
- The **Y axis** label reflects the physical unit of the stream (see table above).
- The **legend** appears to the right of the graph and lists each channel name.
- The last **50 data points** per channel are shown; the window slides as new data arrives.

---

## Stream Toggle Bar

At the bottom of the page is a checkbox row — one per stream. Use these to **show or hide entire streams** across all graphs at once.

{{< hint info >}}
📸 **Screenshot placeholder** — *Stream toggle bar with some streams unchecked*
{{< /hint >}}

| Control | Effect |
|---|---|
| Checkbox **checked** | Stream's graph panel renders data |
| Checkbox **unchecked** | Graph panel is hidden (data still collected in the background) |

---

## Data Behaviour

- The UI polls `/emotibit/data` every **500 ms**.
- Timestamps are filtered: only data newer than the last received point is appended, preventing duplicate plotting.
- Stream list is **discovered at page load**. If the device connects after the page loads, refresh the page to detect new streams.

---

## Troubleshooting

**No panels appear at all**
The backend returned no streams on the initial load. Verify:
1. The EmotiBit device is connected and publishing.
2. The backend `/emotibit/data` endpoint returns a non-empty array.
3. Refresh the page after the device is confirmed active.

**A panel shows no data lines**
The stream may exist but have no channel data yet. Wait a few seconds; if the issue persists, check the backend logs for that stream.

**Graphs freeze (stop updating)**
Check the browser console for fetch errors. A network interruption between the UI and backend will halt updates until connectivity is restored — the graphs will resume automatically once the backend is reachable again.
