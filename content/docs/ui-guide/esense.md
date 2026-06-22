---
title: "eSense"
weight: 4
---

# eSense

The eSense page displays live **temperature data** from the eSense earable sensor. It connects to a single device and plots a real-time temperature graph.

{{< figure src="/images/EsensePanel.jpg" alt="Esense Panel" >}}


---

## Layout

The page contains a single **collapsible Temperature panel** that holds the graph.

---

## Temperature Panel

The panel plots **skin temperature in degrees Celsius (°C)** over time, sampled from the eSense device worn in the ear.

{{< hint info >}}
 Screenshot placeholder — Close-up of the Temperature graph showing a smooth temperature curve
{{< /hint >}}

### Graph Details

| Axis | Description |
|---|---|
| **X axis** | Wall-clock time (`HH:MM:SS`) |
| **Y axis** | Temperature (°C) |

- The graph displays the **last 50 data points** in a sliding window.
- Data is fetched from the backend every **500 ms**.
- Only timestamps newer than the last plotted point are appended (no duplicate rendering).

---

## Collapsing the Panel

Click the **Temperature** header to toggle the graph:

- Panel is expanded (graph visible)
- Panel is collapsed

---

## Data Behaviour

The eSense backend endpoint returns a single device object (not an array). Each data entry contains:
- A **timestamp** as `[seconds, nanoseconds]`
- A **sample_data** value representing the temperature reading

The UI deduplicates incoming data by comparing timestamps against the last recorded point, so only genuinely new readings are added to the graph.

---

## Troubleshooting

**The graph is empty**
- Verify the eSense device is paired, connected, and publishing data to the backend.
- Check the browser console for errors on the `/esense/data` endpoint.
- The device may take a few seconds after connection to begin sending valid temperature readings.

**Temperature values look incorrect**
- Ensure the earable is properly seated in the ear canal — a loose fit can cause inaccurate skin temperature readings.
- Allow the sensor a brief warm-up period (typically 30–60 seconds) after placement before trusting the readings.
