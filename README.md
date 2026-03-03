<div align="center">

# 🚦 Learn Plugin
**Self-Assessment Study Plugin for the Memizy Ecosystem**

![Version](https://img.shields.io/badge/Version-1.0.0-blue?style=for-the-badge)
![Supported Items](https://img.shields.io/badge/Supports-note-blueviolet?style=for-the-badge)
![Features](https://img.shields.io/badge/Features-Markdown%20%7C%20Math-success?style=for-the-badge)

<br>

Official learning plugin for reading and reviewing study notes in the OQSE format. It allows you to browse materials by topic and assess your own knowledge using an interactive Traffic-Light Self-Assessment system.

</div>

---

## 📖 About the Plugin

The **Learn Plugin** is designed for seamless reading of text notes (`note` items) and student self-reflection. Instead of traditional testing, users evaluate how well they understand the material after reading it by clicking a colored dot.

### ✨ Key Features
* **Traffic-Light Assessment:** Rate your confidence using colors:
  * 🔴 *Don't Know* * 🟠 *Partially Know* * 🟡 *Almost Know* * 🟢 *Know Well* * **Smart Filtering:** Allows you to hide notes you already know well (Green) and focus only on the problematic ones (Red/Orange).
* **Topic Organization:** If your OQSE set contains `topic` metadata, the plugin automatically generates a neat dropdown menu for filtering.
* **Full Formatting Support:** Integrated **Marked.js** and **MathJax 3** ensure that all Markdown and complex LaTeX math/chemical formulas render flawlessly.
* **Standalone Mode with Memory:** If you open the plugin independently outside the Memizy app, it automatically saves your progress in the browser (`localStorage`). It also provides buttons for exporting and importing your progress.

## 🛠 Technical Specifications (OQSE Manifest)

This plugin requires the study set to contain items of the `note` type.

```json
{
  "id": "https://memizy.github.io/plugin-learn/",
  "name": "Learn Plugin",
  "version": "1.0.0",
  "description": "Browse study set items grouped by topic. Self-assess your knowledge with traffic-light confidence dots.",
  "author": "Memizy",
  "license": "MIT",
  "itemTypes": ["note"],
  "minItems": 1,
  "features": ["markdown", "math"]
}

```

## 🚀 How to Use

### Within the Memizy Ecosystem (Host)

The plugin is fully integrated with `@memizy/plugin-sdk`. Simply open your study set in the Memizy app and select this plugin. Memizy will handle saving your progress to the cloud in the background.

### Standalone Mode

Since it is a pure HTML/JS file with no build step required, you can open it directly in your browser. Just append the `?set=<SET_ID>` parameter to the URL, and the plugin will create a unique key to store your progress so you can pick up exactly where you left off.

---

## 💻 For Developers

The code is written in vanilla JavaScript and requires no bundlers (like Webpack or Vite).

* **Styling:** Pure CSS utilizing CSS variables for easy color scheme customization.
* **MathJax:** Math rendering is handled asynchronously using `MathJax.typesetPromise()` to prevent UI blocking when loading large study sets.
* **Answer Processing:** The SDK sends a `confidence` level (1-3) to the host application based on the selected color, allowing the host (e.g., a Supabase backend) to calculate precise Spaced Repetition statistics.

---

*Created as part of the Memizy open-source ecosystem.*