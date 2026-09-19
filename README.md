# Recipe Card Generator

A Python utility to automatically extract recipe data from `.mcb` archives or `.xml` exports, process ingredients and instructions, and output print-ready HTML/JPG recipe cards.

## Features

- **Multiple Card Layouts**:
  - `_fullrecipe_card`: A5 Landscape layout (210×148mm) featuring title, ingredients, image, and step-by-step instructions.
  - `_fullrecipe_fold`: A4 Portrait foldable sheet (210×296mm) with a 2-page print layout and optional QR code.
  - `_mealcard_qr`: 4:3 compact ratio (200×150mm) optimized for ingredient overviews and direct QR linking.
- **Multilingual / I18N Support**: Choose between pre-configured languages (`en`, `de`, `es`, `fr`, `nl`) for dynamic layout headers ("Ingredients", "Preparation", etc.).
- **Automated Screenshot Rendering**: Uses headless Chromium via Playwright to convert HTML layouts directly into high-quality JPEG cards (95% quality).
- **Smart Formatting**: Automatically scales font sizes based on text volume to prevent overflow and standardizes ingredient measurements.
- **Interactive Cleanup**: Prompts for cleanup preferences to strip intermediate HTML files, generated QR PNGs, XML files, or unzipped archive folders after generation.

---

## Prerequisites & Installation

### 1. Requirements

- **Python**: Version 3.8 or higher installed on your system.

### 2. Dependencies

Install the required Python packages:

```bash
pip install playwright qrcode pillow
```

### 3. Playwright Browser Setup
Playwright requires its dedicated Chromium browser binaries to capture high-resolution screenshots. Run the following command after installing the Python package:

```Bash
playwright install chromium
```

Note: If you skip this step, the script will still generate HTML files, but it will be unable to export the .jpg images.

### 4. Usage Instructions
Place Input Files: Put your .mcb recipe archives or existing .xml export files in the same directory as the script.

Execute Script: Run the main Python script:

```Bash
python convert.py
```

Follow the Interactive Prompts:

Format Selection: Choose which layout(s) you wish to build ([1] Card, [2] Fold, [3] QR, or [4] All).

Language Selection: Select your target language (en, de, es, fr, nl).

Cleanup Options: Select whether to keep or automatically purge intermediate HTML files, Cookmate XML exports, unzipped *_extracted folders, or QR PNGs.

Output: All generated images and cards are neatly saved to the meal-cards/ folder.

File Structure & Processing Flow
recipe_book.mcb (Input archive)

convert.py (Main script)

meal-cards/ (Output directory - auto-created)

001_Recipe_Name_fullrecipe_card.jpg

001_Recipe_Name_fullrecipe_fold.jpg

001_Recipe_Name_mealcard_qr.jpg

During execution, .mcb files are extracted to temporary *_extracted directories, parsed, rendered to HTML, captured as JPEGs via Playwright, and cleaned up based on your selected prompts.

License
This project is completely open source without any restrictions (Unlicense / Public Domain). Feel free to modify, distribute, or use it for any personal or commercial purpose.
