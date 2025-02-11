# Accessibility Guidelines for Developers

## **📌 General Principles**

### **1️⃣ Semantic HTML First**
✅ Use `<button>` instead of `<div>` for clickable elements  
✅ Headings should be in a logical order (`h1 → h2 → h3`, etc.)  
✅ Use `<section>`, `<article>`, `<aside>`, `<nav>`, `<main>`, `<header>`, `<footer>` instead of `<div>`  

### **2️⃣ Keyboard Navigation**
✅ All interactive elements must be focusable (`tabindex="0"` if needed)  
✅ `:focus` styles must be visible and distinct (never remove them!)  
✅ Use `role="menu"` or `role="listbox"` for custom dropdowns, with arrow key navigation  

### **3️⃣ Color & Contrast**
✅ Text contrast ratio: **4.5:1** for normal text, **3:1** for large text  
✅ Ensure color is not the only indicator (e.g., underlined links, visible focus)  
✅ Use tools like [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)  

### **4️⃣ ARIA for Dynamic Components**
✅ **Avoid unnecessary ARIA** when native elements suffice  
✅ Use `aria-live="polite"` for live updates  
✅ `aria-expanded`, `aria-hidden`, `aria-label`, `aria-describedby` for interactive elements  
✅ Always test ARIA with a screen reader (VoiceOver, NVDA, JAWS)  

### **5️⃣ Forms & Inputs**
✅ Labels **must** be associated with inputs (`<label for="id">`)  
✅ Use `aria-required="true"` for required fields  
✅ Errors should have `aria-invalid="true"` and be described with `aria-describedby="error-message"`  
✅ Use `<fieldset>` and `<legend>` for radio groups and checkboxes  

### **6️⃣ Multimedia & Animations**
✅ Provide captions for videos (`<track>` for HTML5 video)  
✅ Ensure animations are **reduced on request** (`prefers-reduced-motion`)  
✅ Avoid auto-playing sounds/videos  

---

## **📌 WordPress + Timber Specific Guidelines**

### **1️⃣ Use WordPress Hooks and Best Practices**
✅ Use `add_theme_support('html5', array('search-form', 'comment-form', 'gallery'))`  
✅ Properly enqueue styles and scripts instead of inline JS  

### **2️⃣ Alt Text for Images (Timber + WordPress)**
✅ Ensure images use `{{ image.alt }}` dynamically  
✅ Avoid using `alt=""` unless the image is purely decorative  

### **3️⃣ Navigation & Skip Links**
✅ Always provide a **"Skip to main content"** link at the top (`href="#main"`)  
✅ Ensure navigation landmarks use `<nav role="navigation">`  

---

## **📌 JavaScript (Vanilla + React + Vue) Guidelines**

### **1️⃣ Avoid Managing Focus Manually Unless Necessary**
✅ Use `document.activeElement` carefully  
✅ `<input autofocus>` is better than setting focus with JS  

### **2️⃣ Custom Components (React & Vue)**
✅ Use `role` attributes appropriately (`role="alert"`, `role="dialog"`, etc.)  
✅ Ensure virtual DOM updates do not break keyboard navigation  
✅ Avoid `div` soup in JSX – use `<button>`, `<ul>`, `<nav>` properly  

### **3️⃣ Event Listeners**
✅ Always bind keyboard events along with click events  
✅ Example:
```js
function handleClick(event) {
  if (event.type === 'click' || event.key === 'Enter' || event.key === ' ') {
    // Do action
  }
}
```
✅ Ensure Vue/React transitions don’t hide elements from screen readers (`aria-hidden="true"` when needed)  

---

# **📌 Step-by-Step Accessibility Testing Guide**

## **🔹 Phase 1: Automated Tests (First Line of Defense)**

### **1️⃣ Run Lighthouse in Chrome DevTools**
- Open DevTools → Audits → Run Accessibility Audit  
- Ensure the score is **90+**  

### **2️⃣ Use axe DevTools (Browser Extension)**
- Identifies ARIA errors, missing alt text, poor color contrast  

### **3️⃣ Test with WAVE (WebAIM Extension)**
- Checks landmarks, headings, ARIA, and contrast  

---

## **🔹 Phase 2: Manual Testing (User-Centric)**

### **1️⃣ Keyboard-Only Navigation**
✅ Test tabbing order (`Tab`, `Shift+Tab`, `Enter`, `Space`, `Arrow Keys`)  
✅ Ensure no "keyboard traps"  

### **2️⃣ Screen Reader Testing**
✅ Test with **NVDA (Windows)**, **VoiceOver (Mac/iOS)**, or **JAWS**  
✅ Ensure meaningful announcements (e.g., "Button expanded" instead of "Button")  

### **3️⃣ Zoom & Text Resizing**
✅ Test zooming at **200% and 400%**  
✅ Ensure layouts don’t break  

### **4️⃣ Test with Reduced Motion**
✅ Enable `prefers-reduced-motion` in DevTools  
✅ Ensure animations stop when requested  

### **5️⃣ Color-Blindness Simulation**
✅ Use [Tota11y](https://khan.github.io/tota11y/) or [Color Oracle](https://colororacle.org/)  

---

## **🔹 Phase 3: User Testing (Real-World Feedback)**
✅ Involve users with disabilities in real-world testing  
✅ Gather feedback from screen reader users  
✅ Conduct usability testing sessions  

---

## **Final Thoughts**
✔ Accessibility isn't just about passing tests – it's about real usability.  
✔ Follow **semantic HTML, ARIA best practices, proper contrast, and keyboard navigation** to ensure true accessibility.  
✔ Automate what you can, but **real user testing is key**.  
