# 🧊 Home Assistant Fridge Health & Degradation Tracker

An automated Home Assistant package that tracks refrigerator performance, detects mechanical degradation, and predicts maintenance needs **without requiring manual inputs**. 

Unlike standard power monitoring that gets skewed by door openings or grocery loading, this package isolates night-idle consumption (02:00–06:00) and uses 30-day statistical medians to accurately measure baseline power drift over time.

---

## ✨ Key Features

* 🤖 **Zero Manual Input:** Baseline self-seeds and ratchets down automatically to learn your fridge’s peak performance.
* 🚪 **Grocery Day Filter:** Auto-detects and isolates heavy usage days using rolling medians without throwing off baseline calculations.
* 🌙 **Controlled Night Window:** Focuses strictly on 02:00–06:00 idle periods (when doors are closed and ambient drift is minimal).
* 🚨 **Multi-Tier Health Alerts:** Multi-stage warnings (`OK` → `Watch` → `Service`) with persistent notifications and automatic recovery tracking.
* 📊 **Monthly Digest:** Sends a summary report on the 1st of every month with health scores and usage stats.

---

## 🛠️ Requirements

1. A smart plug or energy monitor tracking your fridge (e.g., **Shelly PM Mini G3**, **Shelly Plug S**, or any power monitoring plug).
2. Energy sensor exposing total cumulative energy in `kWh` (`state_class: total_increasing`).
3. Home Assistant package support enabled in `configuration.yaml`:

```yaml
homeassistant:
  packages: !include_dir_named packages
