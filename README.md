<div align="center">

# 🎨 CSS Fundamentals: Overflow, Lists & Shadows

**Three hands-on experiments to understand how CSS controls content, markers, and depth**

</div>

---

## 📖 About This Repository

This repository contains mini-projects I built while learning CSS. Each folder holds a single `index.html` file that isolates **one concept**, so the effect of every property is easy to see and experiment with.

No frameworks, no build tools. Just HTML and CSS.

---

## 📑 Table of Contents

1. [Project Structure](#-project-structure)
2. [Experiment 1: The `overflow` Property](#-experiment-1-the-overflow-property)
3. [Experiment 2: Styling Lists with `list-style`](#-experiment-2-styling-lists-with-list-style)
4. [Experiment 3: `box-shadow` and `text-shadow`](#-experiment-3-box-shadow-and-text-shadow)
5. [How to Run](#-how-to-run)
6. [Key Takeaways](#-key-takeaways)
7. [Roadmap](#-roadmap)

---

## 📂 Project Structure

```
css-fundamentals/
│
├── 04-overflow/
│   └── index.html
│
├── 05-css-lists/
│   └── index.html
│
├── 06-shadows/
│   └── index.html
│
└── README.md
```

> 💡 Rename the folders to match your own layout. Each `index.html` is fully standalone.

---

## 📦 Experiment 1: The `overflow` Property

📁 `04-overflow/index.html`

### 🎯 Goal
Understand what happens when content is **larger than its container**, and how to control it.

### 🔑 Concepts Covered

<table>
  <tr>
    <th>Concept</th>
    <th>What it does</th>
  </tr>
  <tr>
    <td><code>overflow: visible</code></td>
    <td>The default. Extra content <b>spills out</b> of the box and may overlap other elements.</td>
  </tr>
  <tr>
    <td><code>overflow: hidden</code></td>
    <td>Extra content is <b>clipped</b> and cannot be reached by the user.</td>
  </tr>
  <tr>
    <td><code>overflow: scroll</code></td>
    <td>Scrollbars are <b>always shown</b>, even when the content fits.</td>
  </tr>
  <tr>
    <td><code>overflow: auto</code></td>
    <td>Scrollbars appear <b>only when needed</b>. Used in this demo.</td>
  </tr>
  <tr>
    <td><code>vw</code> / <code>vh</code> units</td>
    <td>Sizes relative to the viewport: <code>30vw</code> is 30% of the window width, <code>10vh</code> is 10% of its height.</td>
  </tr>
</table>

### 🧪 Code Highlight

```css
.box {
  width: 30vw;
  height: 10vh;
  border: 2px solid black;
  overflow: auto;
}
```

### 🧠 What Happens Here

The box is only `10vh` tall, but it contains a long paragraph. The width is fixed, so the text wraps onto many lines and quickly becomes taller than the box. With `overflow: auto`, the browser adds a **vertical scrollbar** so the user can scroll through the rest of the text.

### 🔬 Try It Yourself

<details>
<summary><b>Click to expand the experiment steps</b></summary>

<br>

1. Open the file as-is and scroll inside the box.
2. Change `overflow: auto` to `overflow: visible`. The text now spills out below the box.
3. Change it to `overflow: hidden`. The extra text disappears and cannot be scrolled to.
4. Change it to `overflow: scroll`. Scrollbars are always visible, even if you shorten the text.
5. Try `overflow-x` and `overflow-y` separately to control each direction on its own.

</details>

---

## 📋 Experiment 2: Styling Lists with `list-style`

📁 `05-css-lists/index.html`

### 🎯 Goal
Learn how to control the **bullet (marker)** of a list, its **type**, **position**, and **image**, using the `list-style` family of properties.

### 🔑 Concepts Covered

<table>
  <tr>
    <th>Property</th>
    <th>What it controls</th>
    <th>Example values</th>
  </tr>
  <tr>
    <td><code>list-style-type</code></td>
    <td>The shape or numbering of the marker</td>
    <td><code>disc</code>, <code>circle</code>, <code>square</code>, <code>decimal</code>, <code>devanagari</code>, <code>none</code></td>
  </tr>
  <tr>
    <td><code>list-style-position</code></td>
    <td>Whether the marker sits outside or inside the item's box</td>
    <td><code>outside</code> (default), <code>inside</code></td>
  </tr>
  <tr>
    <td><code>list-style-image</code></td>
    <td>A custom image used as the marker</td>
    <td><code>url(arrow.png)</code></td>
  </tr>
  <tr>
    <td><code>list-style</code></td>
    <td>Shorthand for all three above</td>
    <td><code>disc inside</code></td>
  </tr>
  <tr>
    <td><code>nav ul li</code></td>
    <td>A descendant selector that targets list items inside a list inside a nav</td>
    <td>n/a</td>
  </tr>
</table>

### 🧪 Code Highlight

```css
nav ul li {
  background-color: yellow;
  border: 2px solid black;
  list-style: disc inside;
}
```

### 🧠 What Happens Here

The `background-color` and `border` make each `<li>` box visible. Because of `list-style: disc inside`, the bullet is drawn **inside** that box, next to the text. With the default `outside` value, the bullet would sit to the left of the yellow box instead.

### 📊 `inside` vs `outside`

<table>
  <tr>
    <th>Value</th>
    <th>Where the bullet appears</th>
    <th>Text wrapping</th>
  </tr>
  <tr>
    <td><code>outside</code></td>
    <td>Outside the item's box, in the margin area</td>
    <td>Wrapped lines align with the first line of text</td>
  </tr>
  <tr>
    <td><code>inside</code></td>
    <td>Inside the item's box, as part of the content</td>
    <td>Wrapped lines go underneath the bullet</td>
  </tr>
</table>

### 🔬 Try It Yourself

<details>
<summary><b>Click to expand the experiment steps</b></summary>

<br>

1. Remove `inside` from `list-style` and watch the bullet jump outside the yellow box.
2. Uncomment `list-style: devanagari;` to see numbering in Devanagari digits. Try `decimal`, `square` or `lower-roman` too.
3. Try `list-style-type: none;` to remove bullets completely. This is the usual first step when building a navigation menu.
4. Note that `list-style-type: "disc";` with quotes does **not** give a disc. The quotes make the marker the literal text `disc`. Use `disc` without quotes.
5. Add an image with `list-style-image: url(your-icon.png);` for a custom bullet.

</details>

---

## 🌗 Experiment 3: `box-shadow` and `text-shadow`

📁 `06-shadows/index.html`

### 🎯 Goal
Add **depth and emphasis** to boxes and text using shadows, and understand each value in the shadow syntax.

### 🔑 Concepts Covered

<table>
  <tr>
    <th>Concept</th>
    <th>What it does</th>
  </tr>
  <tr>
    <td><code>box-shadow</code></td>
    <td>Draws a shadow around an element's box. Supports <code>spread</code> and <code>inset</code>.</td>
  </tr>
  <tr>
    <td><code>text-shadow</code></td>
    <td>Draws a shadow behind text characters. Does not support <code>spread</code> or <code>inset</code>.</td>
  </tr>
  <tr>
    <td><code>padding</code></td>
    <td>Space between the content and the border. Here it makes the box roomy enough to see the shadow clearly.</td>
  </tr>
</table>

### 🧪 Code Highlight

```css
.box {
  border: 2px solid black;
  padding: 34px;
  box-shadow: 5px 15px 5px #70a711;
}

.text-element {
  text-shadow: 10px 5px 3px #e695f7;
}
```

### 🧬 Anatomy of the Shadow Values

<table>
  <tr>
    <th>Part</th>
    <th><code>box-shadow</code> value</th>
    <th><code>text-shadow</code> value</th>
    <th>Meaning</th>
  </tr>
  <tr>
    <td>1. X offset</td>
    <td align="center"><code>5px</code></td>
    <td align="center"><code>10px</code></td>
    <td>Moves the shadow right (negative moves it left)</td>
  </tr>
  <tr>
    <td>2. Y offset</td>
    <td align="center"><code>15px</code></td>
    <td align="center"><code>5px</code></td>
    <td>Moves the shadow down (negative moves it up)</td>
  </tr>
  <tr>
    <td>3. Blur radius</td>
    <td align="center"><code>5px</code></td>
    <td align="center"><code>3px</code></td>
    <td>Higher values make the edge softer. <code>0</code> gives a sharp edge</td>
  </tr>
  <tr>
    <td>4. Color</td>
    <td align="center"><code>#70a711</code> (green)</td>
    <td align="center"><code>#e695f7</code> (pink)</td>
    <td>The color of the shadow</td>
  </tr>
</table>

> ℹ️ `box-shadow` has an optional fifth value, **spread**, placed after the blur radius. It is not used in this demo.

### 🔬 Try It Yourself

<details>
<summary><b>Click to expand the experiment steps</b></summary>

<br>

1. Set the blur to `0` and see a hard, flat shadow.
2. Use negative offsets, such as `-5px -15px`, to move the shadow up and to the left.
3. Add the keyword `inset` to the `box-shadow` so the shadow appears inside the box.
4. Add a fifth value to `box-shadow` (for example `5px 15px 5px 10px #70a711`) to grow the shadow with spread.
5. Stack multiple shadows by separating them with commas: `text-shadow: 2px 2px red, 4px 4px blue;`

</details>

---

## 🚀 How to Run

No installation needed.

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/<your-repo-name>.git

# 2. Move into the project
cd <your-repo-name>

# 3. Open any experiment in your browser
open 04-overflow/index.html      # macOS
start 04-overflow/index.html     # Windows
xdg-open 04-overflow/index.html  # Linux
```

💡 **Tip:** Use the VS Code **Live Server** extension to see changes instantly as you edit.

---

## 🎓 Key Takeaways

<table>
  <tr>
    <td>✅</td>
    <td><code>overflow: auto</code> adds scrollbars only when the content is too big for its container.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>Use <code>min-height</code> when the container should grow, and <code>overflow</code> when the size must stay fixed.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td><code>list-style</code> is a shorthand for type, position, and image of a list marker.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td><code>list-style-position: inside</code> puts the bullet inside the item's box.</td>
  </tr>
  <tr>
    <td>✅</td>
    <td>Shadows follow the pattern <code>x-offset y-offset blur color</code>, and <code>box-shadow</code> also supports spread and inset.</td>
  </tr>
</table>

---

## 🗺️ Roadmap

- [x] `display` property
- [x] Viewport units and box model
- [x] CSS specificity
- [x] `overflow`
- [x] Lists and `list-style`
- [x] `box-shadow` and `text-shadow`
- [ ] Flexbox
- [ ] CSS Grid
- [ ] Positioning (`relative`, `absolute`, `fixed`, `sticky`)
- [ ] Media queries and responsive design
- [ ] Transitions and animations

---

<div align="center">

### ⭐ If you found this helpful, consider giving the repo a star!

Made with ❤️ while learning CSS

</div>
