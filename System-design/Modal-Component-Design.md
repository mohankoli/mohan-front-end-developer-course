# 🧩 Reusable Modal Component Design (with Focus Trap, Keyboard Navigation & Portal Mounting)

---

## 🕐 0–5 min — Requirements Gathering

**Before I start, I want to confirm a few things:**
- Should the modal support **multiple modals** open at once?
- Should **clicking outside** or **pressing ESC** close the modal?
- Should **animations** (fade/slide) be supported?
- Is this part of a **design system** (so we need reusability and theme support)?
- Are we targeting **accessibility compliance** (WCAG, keyboard users, screen readers)?

**Requirements Summary:**
- Reusable and mounted via a **Portal** (outside DOM hierarchy)
- Trap **focus within modal content**
- Support **closing via Esc key** or **backdrop click**
- Be accessible with **ARIA roles**
- Handle **multiple modals safely** and restore scroll/focus

---

## ⚙️ 5–10 min — Components Breakdown

### **Core Components**

| Component | Responsibility |
|------------|----------------|
| **Modal** | Main container, manages open/close, accessibility, and lifecycle |
| **Backdrop** | Overlay layer that dims background and handles click-outside events |
| **Portal** | Mounts modal into `document.body` or `#modal-root` |
| **FocusTrap** | Keeps tab focus inside modal |
| **ModalManager (optional)** | Handles stacking, scroll lock, and z-index for nested modals |

> “This separation keeps the logic reusable — `Backdrop` or `Portal` can also be used by dropdowns or tooltips.”

---

## 🧠 10–15 min — State & Data Management

### **Local State**
isOpen: boolean
previousActiveElement: HTMLElement | null
focusableElements: HTMLElement[]

## 🧠 10–15 min — State & Data Management

### **Hooks**
- **`useEffect`** → manage focus on mount/unmount  
- **`useRef`** → store modal DOM node  

> “I’ll handle all open/close logic inside the Modal and communicate via props to parent.  
> When opened, I’ll disable background scroll, trap focus, and restore focus on close.”

---

## 🧭 15–20 min — Interactions Flow

### **Opening**
1. Register modal with `ModalManager`
2. Lock body scroll (`overflow: hidden`)
3. Save current focus
4. Move focus to first focusable element inside modal

### **User Actions**
- **Tab / Shift+Tab** → cycle focus inside modal  
- **ESC** → triggers `onClose()`  
- **Backdrop click** → triggers `onClose()` if enabled  

### **Closing**
1. Unregister from manager  
2. Restore focus to previous element  
3. Unlock scroll  
4. Unmount modal portal  

> “A flow diagram can help visualize these transitions.”

---

## 🚀 20–25 min — Performance & Accessibility

### **Performance**
- Use **React Portal** to avoid reflow issues  
- **Lazy-mount** modal content (only render when `isOpen = true`)  
- Use **memoization** to minimize re-renders  
- **Batch focus computations** to reduce DOM overhead  

### **Accessibility (A11y)**
- `role="dialog"` and `aria-modal="true"`  
- `aria-labelledby` or `aria-label` for title  
- Background elements marked `aria-hidden="true"`  
- Focus trap + ESC ensures **keyboard navigation**  
- High contrast **backdrop** for visibility  

> “Accessibility is critical — the modal must behave identically for keyboard and screen-reader users.”

---

## ⚖️ 25–30 min — Trade-offs & Extensions

### **Trade-offs**

| Choice | Pros | Cons |
|--------|------|------|
| **JS Focus Trap** | Works in all browsers | Adds complexity |
| **Native `<dialog>`** | Simpler implementation | Limited styling/flexibility |
| **Global Manager** | Simplifies stacking | Adds shared state |
| **CSS Animations** | Lightweight | Limited control |
| **JS Animations** | More control | Performance cost |
| **Accessibility Layer** | Better UX | Increases code size |

---

### **Possible Extensions**
- Support **nested modals** (stack manager)  
- Add **transitions** with Framer Motion  
- Provide **theme & size variants** (small, large, fullscreen)  
- Support **mobile gestures**


> “My modal design focuses on **separation of concerns** — rendering via a **Portal**, ensuring **accessibility** with focus trap and ARIA roles, handling **performance efficiently**, and providing **reusability** across the app.  
> In production, I’d wrap this into a **design system component library** for consistent usage.”
