# 🧩 Toast / Notification System Design  
**(Queueing, Stacking, Auto-Dismiss, Pause on Hover)**

---

## 🕐 0–5 min — Requirements Gathering

**Questions to confirm:**
- Should multiple toasts stack or queue?
- Should auto-dismiss be configurable per toast?
- Should hover pause the dismiss timer?
- Should there be priority/preemption (e.g., error > info)?
- Do we need accessibility compliance (ARIA, screen readers)?

**Requirements Summary:**
- Show short-lived notifications (success, error, info, warning)
- Support stacking + queueing
- Auto-dismiss with configurable timeout
- Pause on hover or focus
- Accessible (role="status", aria-live)
- Reusable API and theme support

---

## ⚙️ 5–10 min — Components Breakdown

| Component | Responsibility |
|------------|----------------|
| **ToastManager** | Central state; handles queue, stacking, dismissal |
| **ToastContainer** | Renders visible toasts (usually via Portal) |
| **ToastItem** | Individual notification; timer, pause/resume logic |
| **Timer Engine** | Tracks timeouts and pause states |
| **Accessibility Layer** | Announces updates for screen readers |

> “Separation allows reusability — ToastContainer can be reused per section or globally.”

---

## 🧠 10–15 min — State & Data Management

**Local State:**
- `toasts[]`: visible list  
- `queue[]`: pending notifications  
- `maxVisible`: limit on stack size  
- `paused`: boolean for hover state  

**Hooks & Logic:**
- `useEffect` → handle mount/unmount timers  
- `useRef` → store timeout IDs  
- `useCallback` → debounce queue operations  

> “Manager promotes queued toast when a visible one closes; timers resume on hover leave.”

---

## 🧭 15–20 min — Interaction Flow

**Creation**
1. `toastManager.show({ type, message, timeout })`
2. If stack < `maxVisible` → render immediately, else queue.

**During Display**
- Countdown timer auto-dismisses.
- Hover → pause timer.
- Leave hover → resume timer.

**On Dismiss**
- Remove from visible list.
- Promote next from queue (if any).

---

## 🚀 20–25 min — Performance & Accessibility

**Performance**
- Only render visible toasts.
- Use memoized list rendering.
- Avoid frequent reflows (CSS transitions for animation).

**Accessibility**
- `role="status"` or `role="alert"` for screen readers.
- `aria-live="polite"` announcements.
- Focus management for actionable toasts.
- High-contrast & timeout warnings for better UX.

---

## ⚖️ 25–30 min — Trade-offs & Extensions

| Choice | Pros | Cons |
|--------|------|------|
| Global Manager | Central control | Shared state complexity |
| Local Container | Scoped usage | Multiple stacks possible |
| JS Timers | Precise control | Slight overhead |
| CSS Animations | Lightweight | Less lifecycle control |

**Extensions:**
- Support priority-based queueing  
- Group by toast type (error/info)  
- Add undo/action buttons  
- Theme + motion variants (slide, fade)  
- Persistent toasts (no auto-dismiss)

---

**Summary:**  
A reusable, accessible Toast system that manages queueing, stacking, and dismissal efficiently with strong UX and accessibility guarantees.
