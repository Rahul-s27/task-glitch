# 🧠 Task Glitch — Bug Fix Summary

This repository contains fixes for a set of intentionally introduced bugs in a React-based Task Management application.  
The focus of this work was to improve **stability, correctness, and user experience** without adding new features.

---

## ✅ Bugs Fixed

### 🐞 Bug 1 — Double Fetch on Page Load
**Issue:** Tasks were fetched twice on initial load due to React StrictMode and duplicate effect execution.  
**Fix:** Ensured task-loading logic runs only once on mount, preventing duplicate network calls and duplicated task data.

---

### 🐞 Bug 2 — Undo Snackbar State Leak
**Issue:** Deleted tasks could be restored incorrectly after the undo snackbar closed due to stale state.  
**Fix:** Cleared temporary deleted-task state when the snackbar closes so undo is only possible during the active snackbar window.

---

### 🐞 Bug 3 — Unstable Sorting (ROI Ties)
**Issue:** Tasks with identical ROI and priority reordered randomly on re-renders, causing UI flicker.  
**Fix:** Added a deterministic alphabetical title tie-breaker to ensure stable and predictable task ordering.

---

### 🐞 Bug 4 — Multiple Dialogs Opening
**Issue:** Clicking Edit or Delete triggered both the action dialog and the View dialog due to event bubbling.  
**Fix:** Stopped event propagation in Edit and Delete button handlers to ensure only the intended dialog opens.

---

### 🐞 Bug 5 — ROI Calculation & Validation Errors
**Issue:** Invalid inputs (e.g., time = 0 or missing values) caused `Infinity` or `NaN` ROI values and UI issues.  
**Fix:** Implemented defensive ROI validation and consistent formatting to ensure safe calculations and stable UI behavior.

---

## 🧪 Verification Checklist

- No duplicate task fetches on page load  
- Stable task ordering across renders and reloads  
- Undo works only while snackbar is visible  
- Dialogs open independently without overlap  
- ROI values are always valid (no `Infinity` / `NaN`)  
