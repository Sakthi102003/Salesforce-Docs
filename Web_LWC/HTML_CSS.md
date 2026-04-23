# HTML, CSS, and Apex Recursion

## Apex Trigger Recursion
Trigger recursion occurs when a trigger performs an action that causes the same trigger (or another trigger on the same object) to execute again, potentially leading to an infinite loop and hitting governor limits.
- **Prevention:** Use a static boolean variable in a handler class to track if the trigger has already executed within the current transaction.

---

## Web Development Basics

### HTML and CSS
HTML provides the structure of a webpage, while CSS (Cascading Style Sheets) defines the visual presentation.

### Types of CSS:
1. **Inline CSS:** Applied directly to an HTML element using the `style` attribute.
2. **Internal CSS:** Defined within a `<style>` tag inside the `<head>` section of an HTML document.
3. **External CSS:** Defined in a separate `.css` file and linked to the HTML document. This is the preferred method for maintainability.

### CSS Selectors:
1. **ID Selector:** Targets a single element with a specific `id` attribute (e.g., `#abc`).
2. **Class Selector:** Targets one or more elements with a specific `class` attribute (e.g., `.pqr`).
3. **Tag (Element) Selector:** Targets all elements of a specific type (e.g., `div`, `p`, `h1`).

---

## Key CSS Concepts

### 1. The Box Model
Every HTML element is essentially a box. The Box Model consists of:
- **Content:** The actual text or image.
- **Padding:** Clear space around the content.
- **Border:** A line surrounding the padding.
- **Margin:** Clear space outside the border.

### 2. Layout and Responsiveness
- **Floats:** A traditional layout property used to push elements to the left or right of their container.
- **Media Queries:** Used to apply different styles depending on the device's screen size (e.g., mobile vs. desktop), making the page **responsive**.