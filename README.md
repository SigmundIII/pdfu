# 📄 pdfu

![Bash](https://img.shields.io/badge/Shell-Bash-4EAA25?style=flat-square&logo=gnu-bash&logoColor=white)
![macOS](https://img.shields.io/badge/OS-macOS-000000?style=flat-square&logo=apple&logoColor=white)
![Linux](https://img.shields.io/badge/OS-Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)

`pdfu` is a lightweight, command-line PDF utility that allows you to manage and manipulate PDF files directly from your terminal. It includes built-in safeguards, such as enforcing `.pdf` extensions and prompting before overwriting existing files.

---

## ✨ Features

*   **✂️ Extract & Split**: Isolate specific page ranges or break a document into multiple files.
*   **🔗 Merge**: Combine multiple PDF files into one seamless document.
*   **🗜️ Compress**: Shrink PDF file sizes using standard quality presets.
*   **🖼️ Images to PDF**: Convert lists or folders of images (`.jpg`, `.png`, `.webp`, etc.) into a single PDF, complete with a visual progress bar.
*   **ℹ️ Info**: Quickly view a file's size, PDF version, and total page count.

---

## 🚀 Installation

### 1. Install Dependencies

**macOS (via Homebrew):**
```bash
brew install ghostscript
```
*(Note: `pdfu` uses the native `sips` tool for image processing on macOS, so no extra image libraries are required).*

**Linux (Debian/Ubuntu):**
```bash
sudo apt update
sudo apt install ghostscript imagemagick
```

### 2. Setup pdfu
First, make the script executable:
```bash
chmod +x pdfu
```

Choose one of the following methods to run the tool:

*   **Option A: System-wide (Recommended)**  
    Move it to your binary folder to run it from anywhere:
    ```bash
    sudo mv pdfu /usr/local/bin/
    ```
*   **Option B: Shell Alias**  
    Add an alias to your `~/.zshrc` or `~/.bashrc` to run it from anywhere without moving the file:
    ```bash
    alias pdfu="/full/path/to/pdfu"
    ```
*   **Option C: Local Execution**  
    Keep the file in its current folder and run it directly:
    ```bash
    ./pdfu help
    ```

---

## 🛠️ Usage & Commands

Run `pdfu help` at any time to view the usage menu.

### 📄 Document Manipulation
*   **Extract Pages**  
    `pdfu extract <input.pdf> <output.pdf> <start-end> [start-end...]`
*   **Split PDF**  
    `pdfu split <input.pdf> <output.pdf> <start-end> [start-end...]`  
    *(Automatically appends `_1`, `_2` to the output name for multiple ranges).*
*   **Merge PDFs**  
    `pdfu merge <output.pdf> <input1.pdf> <input2.pdf> [input...]`

### 🗜️ Optimization & Conversion
*   **Compress PDF**  
    `pdfu compress [-v|--verbose] <input.pdf> <output.pdf> [quality]`  
    *(Quality options: `screen`, `ebook` (default), or `printer`).*
*   **Images to PDF**  
    `pdfu img2pdf <output.pdf> <image_or_dir> [image_or_dir...]`  
    *(Automatically identifies and skips unsupported formats or broken images).*

### 🔍 Utility
*   **File Info**  
    `pdfu info <input.pdf>`

---

## 🧪 Testing

The project includes an automated bash script (`test_pdfu.sh` / `unit-tests`) to verify all utility functions.

1.  Place sample PDFs and images in the `test/input` directory.
2.  Run the test script:
    ```bash
    ./unit-tests
    ```
3.  All generated files and test logs will be outputted cleanly into the `test/output` directory for review.