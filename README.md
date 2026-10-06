# pdfu

`pdfu` is a command-line PDF utility that allows you to manage and manipulate PDF files directly from your terminal. It includes built-in safeguards, such as ensuring output files always use the `.pdf` extension and prompting you before overwriting existing files.

## Dependencies
To use `pdfu`, your system requires the following tools:
*   **Ghostscript (`gs`)**: Required for core PDF manipulations like extracting, merging, compressing, and splitting.
*   **Image Converter**: Either `sips` (macOS native), `magick`, or `convert` (ImageMagick) is required for the `img2pdf` command.

## Commands
You can view the usage menu at any time by running `pdfu help`.

*   **Extract Pages**: `pdfu extract <input.pdf> <output.pdf> <start-end> [start-end...]`
    *   Extracts specific page ranges from a PDF and outputs them into a new, single PDF file.
*   **Merge PDFs**: `pdfu merge <output.pdf> <input1.pdf> <input2.pdf> [input...]`
    *   Combines multiple PDF files into one final document.
*   **File Info**: `pdfu info <input.pdf>`
    *   Displays the PDF's file size, version, and total page count.
*   **Compress PDF**: `pdfu compress [-v|--verbose] <input.pdf> <output.pdf> [quality]`
    *   Reduces the file size of a PDF. 
    *   Quality options include `screen` (lowest size and quality), `ebook` (the default setting), and `printer` (high quality). 
*   **Split PDF**: `pdfu split <input.pdf> <output.pdf> <start-end> [start-end...]`
    *   Separates a PDF into multiple distinct files based on the specified page ranges. 
    *   When multiple ranges are provided, it automatically appends a numbered suffix (e.g., `_1`, `_2`) to the base output file name.
*   **Images to PDF**: `pdfu img2pdf <output.pdf> <image_or_dir> [image_or_dir...]`
    *   Compiles a list of individual image files or entire directories into a single PDF document.
    *   Supported image formats are `.jpg`, `.jpeg`, `.png`, `.gif`, `.bmp`, `.tif`, `.tiff`, and `.webp`.
    *   Features a visual terminal progress bar and automatically identifies and skips unsupported file formats or broken images.

## Testing
The project includes an automated bash script to test the utility's functions.
*   The script reads sample PDFs and images from a `test/input` directory.
*   It runs a sequence of commands covering `help`, `info`, `extract`, `merge`, `compress`, `split`, and `img2pdf`.
*   All test results and generated files are cleanly outputted into a freshly generated `test/output` directory for review.