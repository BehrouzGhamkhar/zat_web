---
title: "UI Guide"
weight: 2
bookCollapseSection: true
---

# UI Guide

This section documents every screen and panel in the Session Manager interface. Use the sidebar to navigate to a specific component, or read the pages in order for a complete walkthrough.

## Overview

The Session Manager is a React-based web application for monitoring live sensor streams and controlling data recording sessions. It connects to a backend server that aggregates data from multiple sensor devices.

The interface is divided into two areas:

- **Side Panel (navigation)** — links to each sensor view and the saver controls
- **Main Content Area** — displays the active page (graphs, controls, etc.)

{{< hint info >}}
Screenshot placeholder — Full app layout showing side panel and main content area
{{< /hint >}}

## Pages at a Glance

| Page | Purpose |
|---|---|
| [Home]({{< relref "/docs/ui-guide/home" >}}) | Landing screen shown on startup |
| [Movella Sensors]({{< relref "/docs/ui-guide/movella" >}}) | Live IMU data from up to 5 Movella sensors |
| [EmotiBit]({{< relref "/docs/ui-guide/emotibit" >}}) | Live biometric streams from the EmotiBit device |
| [eSense]({{< relref "/docs/ui-guide/esense" >}}) | Live temperature from the eSense earable |
| [Saver Panel]({{< relref "/docs/ui-guide/saver-panel" >}}) | Topic selection and recording start/stop |
