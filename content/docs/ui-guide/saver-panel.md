---
title: "Saver Panel"
weight: 5
---

# Saver Panel

The Saver Panel is the recording control centre of the Session Manager. From here you can **select which ROS topics to record** and **start or stop a recording session**.

{{< figure src="/images/SaverPanel.jpg" alt="Saver Panel" >}}


---

## Layout

The panel is divided into three sections from top to bottom:

1. **Topic Configuration** — choose which topics to include in the recording
2. **Recording Controls** — START / STOP buttons with a live status indicator
3. **Status Message** — feedback from the backend after each action

---

## Topic Configuration

{{< figure src="/images/TopicConfig.jpg" alt="Topic Configuration" >}}


### Topic List

The topic list is fetched from the backend every **5 seconds** and shows all currently known ROS topics. Each row contains:

| Element | Description |
|---|---|
| **Checkbox** | Select or deselect the topic for recording |
| **Topic name** | Full ROS topic path (e.g. `/movella/sensor_1`) |
| **Message type** | Shortened ROS message type shown in parentheses |
| **Status badge** | 🟢 **Active** — topic is currently publishing; 🔴 **Inactive** — no data |

### Selecting Topics

- **Check individual topics** to record only those data streams.
- **Leave all boxes unchecked** to record *all* available topics (default behaviour).

### Sending the Configuration

{{< figure src="/images/Send.jpg" alt="Topic Configuration" >}}

After making your selection, click **Send**. The status message at the bottom of the panel will confirm the configuration was accepted by the backend.



---

## Recording Controls

{{< figure src="/images/StartStop.jpg" alt="Topic Configuration" >}}


### LED Indicator

The small LED circle next to the "Recording Controls" heading shows the current recording state:

| LED State | Meaning |
|---|---|
| 🟢 Green (pulsing) | Recording is **active** |
| ⚪ Grey / off | Recording is **stopped** |

The recording status is also polled from the backend every **5 seconds**, so if another client or process changes the recording state, the indicator will update automatically within a few seconds.

### START Button

Click **START** to begin recording the configured topics. The LED will turn green and the status message will update to confirm.

{{< hint warning >}}
⚠️ Make sure you have sent your topic configuration (clicked <b>Send</b>) before pressing START. Starting a recording without sending a configuration will record all available topics by default.
{{< /hint >}}

### STOP Button

Click **STOP** to end the current recording. The LED will return to grey and the status message will confirm the session has stopped.

---

## Status Message

The yellow status bar at the bottom of the panel displays feedback messages from the backend:

| Message type | Example |
|---|---|
| Success | *"Recording started."* / *"Topics updated: Success"* |
| Default config notice | *"Default configuration: recording all available topics."* |
| Error | *"Failed to contact backend."* / *"Failed to load topics from backend."* |

{{< hint info >}}
Screenshot placeholder — Yellow status bar showing a success message after clicking START
{{< /hint >}}

---

## Typical Workflow

A standard recording session looks like this:

1. Open the **Saver Panel** from the side navigation.
2. Wait for the topic list to populate (a few seconds).
3. Check the topics you want to record, or leave all unchecked for all topics.
4. Click **Send** — confirm the status message shows success.
5. Click **START** — confirm the LED turns green.
6. Run your experiment.
7. Click **STOP** when the session is complete.

---

## Troubleshooting

**Topic list is empty**
The backend may not have returned any topics yet. Wait a few seconds for the automatic refresh. If the list remains empty, check that the backend is running and the `/saver/topics/availability` endpoint is reachable.

**Status badge shows 🔴 Inactive for all topics**
No ROS nodes are currently publishing. Start the relevant sensor nodes before configuring a recording session.

**Clicking START shows "Failed to contact backend"**
Verify the backend is running and the `BASE_URL` in `config.js` matches the backend address and port.

**LED stays grey after clicking START**
The recording command may have failed silently. Check the status message for an error and inspect the browser console for network errors.
