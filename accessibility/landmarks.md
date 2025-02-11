# Landmarks

### **How to Use Landmarks for Accessibility**  
Landmarks in HTML help assistive technologies (like screen readers) navigate a website efficiently. They create **structured, meaningful regions** so users can jump between sections easily.

---

## **🔹 Key Landmarks & How to Use Them**
### **1️⃣ `<header>` (Role: `banner`)**
🔹 **Usage:** The main website header, usually containing the logo, navigation, and site-wide branding.  
🔹 **Rules:**  
✅ There should be **only one** `<header>` landmark per page (except inside `<article>` or `<section>`)  
✅ Avoid placing multiple `<header>` elements at the top level  

👉 **Example:**  
```html
<header role="banner">
  <h1>My Website</h1>
  <nav>
    <ul>
      <li><a href="/about">About</a></li>
      <li><a href="/contact">Contact</a></li>
    </ul>
  </nav>
</header>
```

---

### **2️⃣ `<nav>` (Role: `navigation`)**
🔹 **Usage:** For major navigation links (e.g., main menu, breadcrumbs, sidebar navigation)  
🔹 **Rules:**  
✅ Always include **`aria-label`** or **`aria-labelledby`** when multiple `<nav>` elements exist  
✅ Do not use `<nav>` for every group of links—only major navigation areas  

👉 **Example:**  
```html
<nav role="navigation" aria-label="Main Menu">
  <ul>
    <li><a href="/home">Home</a></li>
    <li><a href="/services">Services</a></li>
    <li><a href="/contact">Contact</a></li>
  </ul>
</nav>
```

---

### **3️⃣ `<main>` (Role: `main`)**
🔹 **Usage:** Contains the main content of the page  
🔹 **Rules:**  
✅ Each page should have **only one**
✅ Avoid nesting `<main>` inside other elements  

👉 **Example:**  
```html
<main role="main">
  <h1>Welcome to Our Museum</h1>
  <p>Explore our latest exhibitions and collections.</p>
</main>
```

---

### **4️⃣ `<aside>` (Role: `complementary`)**
🔹 **Usage:** For **side content** (related but not essential) like sidebars, related articles, or widgets  
🔹 **Rules:**  
✅ Use **only if the content enhances the main content**  
✅ Avoid using `<aside>` for purely decorative elements  

👉 **Example:**  
```html
<aside role="complementary">
  <h2>Related Articles</h2>
  <ul>
    <li><a href="#">The History of Art</a></li>
    <li><a href="#">Famous Artists</a></li>
  </ul>
</aside>
```

---

### **5️⃣ `<footer>` (Role: `contentinfo`)**
🔹 **Usage:** The site-wide footer with copyright, contact, and legal information  
🔹 **Rules:**  
✅ Use **only one `<footer>` at the page level**  
✅ Can be repeated inside `<article>` for self-contained content  

👉 **Example:**  
```html
<footer role="contentinfo">
  <p>&copy; 2024 Museum Name. All rights reserved.</p>
  <nav aria-label="Footer Navigation">
    <ul>
      <li><a href="/privacy">Privacy Policy</a></li>
      <li><a href="/terms">Terms of Service</a></li>
    </ul>
  </nav>
</footer>
```

---

### **6️⃣ `<section>` (Role: `region`)**
🔹 **Usage:** To define major sections of content (e.g., feature areas, long-form articles)  
🔹 **Rules:**  
✅ Use **`aria-labelledby`** to provide a descriptive label  
✅ Only use when it **adds meaning**, not just for styling  

👉 **Example:**  
```html
<section role="region" aria-labelledby="events-heading">
  <h2 id="events-heading">Upcoming Events</h2>
  <p>Join our museum events happening this month.</p>
</section>
```

---

### **7️⃣ `<article>` (Role: `article`)**
🔹 **Usage:** For self-contained content (e.g., blog posts, news items, comments)  
🔹 **Rules:**  
✅ Should be **meaningful as a standalone unit**  
✅ Can be used multiple times per page  

👉 **Example:**  
```html
<article role="article">
  <h2>New Exhibition: Modern Art</h2>
  <p>Explore our latest collection of modern artworks.</p>
</article>
```

---

## **🔹 Best Practices**
✅ **Every page should have**:  
- **One `<header>`**  
- **One `<main>`**  
- **One `<footer>`**  
- **One or more `<nav>` if needed**  
- **Additional `<aside>` and `<section>` when useful**  

✅ **Use ARIA when necessary**  
- Example: Multiple `<nav>` elements should have `aria-label="Primary Navigation"` and `aria-label="Footer Navigation"`  

✅ **Use screen reader testing**  
- Test with **NVDA, VoiceOver, or JAWS** to check how landmarks work  

---

## **🔹 Why Landmarks Matter**
✅ **Improves screen reader navigation** (users can jump directly to sections)  
✅ **Enhances SEO** (semantic HTML is favored by search engines)  
✅ **Provides a structured, accessible experience**  
