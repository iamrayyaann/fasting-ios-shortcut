# Configuration Guide

This document explains all configurable variables in the Fasting Reminder shortcut.

## Variables

### `setupState`

| Property | Value |
|----------|-------|
| **Type** | Boolean |
| **Default** | `False` |
| **Location** | Top of shortcut (Setup Section) |

**Purpose:** Controls the initial setup mode for granting permissions.

| Value | Behavior |
|-------|----------|
| `True` | Enables setup mode — the shortcut will prompt for alarm deletion permissions |
| `False` | Normal operation mode — the shortcut runs without setup prompts |

**When to use:**
- Set to `True` only during first-time setup
- Return to `False` after granting "Delete Always" permission

---

### `Fast Everyday`

| Property | Value |
|----------|-------|
| **Type** | Boolean |
| **Default** | `False` |
| **Location** | Setup Section |

**Purpose:** Overrides the fast calendar to treat every day as a fasting day.

| Value | Behavior |
|-------|----------|
| `True` | Alarms are set daily regardless of the Islamic calendar |
| `False` | Alarms are only set on days that match enabled fasts |

**When to use:**
- Six Days of Shawwal (choose any 6 days)
- Consecutive voluntary fasting
- Making up missed fasts (Qada)
- Any custom fasting schedule

> ⚠️ **Remember** to set this back to `False` when you're done with your voluntary fasting period.

---

## Fast List

The shortcut contains a list of Islamic fasts that can be individually enabled or disabled.

### How to Modify

1. Open the Fasting Reminder shortcut in edit mode
2. Scroll to the **Fast List** section
3. Remove or comment out any fasts you do not observe

### Available Fasts

| Fast | Hijri Date(s) | Enabled by Default |
|------|---------------|-------------------|
| **Ramadan** | 1–30 Ramadan | ✅ Yes |
| **Ashura** | 10 Muharram | ✅ Yes |
| **Day of Arafah** | 9 Dhul Hijjah | ✅ Yes |
| **Ayyam al-Beed** | 13, 14, 15 of each month | ✅ Yes |
| **Mondays** | Every Monday | ✅ Yes |
| **Thursdays** | Every Thursday | ✅ Yes |

### Recommended Configurations

#### Ramadan Only
Remove all fasts except Ramadan from the list.

#### Sunnah Fasts
Keep all defaults enabled.

#### Minimal Setup
Keep only:
- Ramadan
- Day of Arafah
- Ashura

---

## Automation Timing

The shortcut relies on three iOS automations. While the exact times are flexible, they must fall within these ranges:

| Automation | Recommended Time | Acceptable Range | Purpose |
|------------|------------------|------------------|---------|
| Suhoor Alarm | 3:00 AM | 2:00 AM – 4:00 AM | Sets alarm before Fajr |
| Iftar Alarm | 5:00 PM | 4:00 PM – 6:00 PM | Sets alarm before Maghrib |
| Cleanup | 8:30 PM | 8:00 PM – 9:00 PM | Deletes expired alarms |

### Timing Considerations

- **Suhoor automation** should run well before the earliest possible Fajr time in your location
- **Iftar automation** should run before Maghrib to give you time to prepare
- **Cleanup automation** should run after Iftar to remove that day's alarms

---

## Troubleshooting Configuration Issues

| Problem | Likely Cause | Solution |
|---------|--------------|----------|
| Alarms set every day | `Fast Everyday` is `True` | Set to `False` |
| No alarms being set | All fasts removed from list | Re-add desired fasts |
| Permission popup keeps appearing | `setupState` is `True` | Set to `False` |
| Wrong prayer times | Location services disabled | Enable location access for Shortcuts |

---

## Resetting to Defaults

To reset the shortcut to default configuration:

1. Delete the current shortcut
2. Re-import from the [original iCloud link](https://www.icloud.com/shortcuts/3e79d49d497c449cb568866628bb948c)
3. Follow the setup process again
