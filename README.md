# Grayscale & Binarization in Pure Python (No External Libraries)

This project converts a color image to:

Grayscale (0–255), and

Binary (0 / 255, black & white),

using only Python’s standard library for image parsing (no Pillow/OpenCV/NumPy in the core logic). The notebook also includes matplotlib previews (bundled in Colab).

# Highlights

Input: BMP 24/32-bit BI_RGB (uncompressed) or PPM P3 (ASCII)

Output: PGM P2 (grayscale), PGM P2 (binary), PBM P1 (binary; 1=black, 0=white)

Threshold: fixed (default 127) or Otsu (available in the PPM path)

Environment: Google Colab, no extra installs required

# How to use (Colab)

Upload a BMP 24/32-bit BI_RGB (or a PPM P3).

Run the validation cell (accepts DIB headers 40/108/124).

Run the processing cell to produce:

gray_from_bmp.pgm (grayscale),

binary_from_bmp.pgm and binary_from_bmp.pbm (binary, threshold=127 by default).

Use the plotting cell to preview original BMP, grayscale, and binary images.

(Optional) Adjust the threshold in the provided cell and re-plot.

Export the generated files as a .zip.

# How it works (core logic)

Grayscale (luma approximation):
Y = 0.299·R + 0.587·G + 0.114·B (clamped to [0,255])

Binarization (fixed threshold):
pixel = 255 if Y ≥ threshold else 0

PBM P1 convention: 1 = black, 0 = white

# Supported formats

BMP: uncompressed (BI_RGB=0), 24 or 32 bits per pixel; DIB header size 40 / 108 / 124

PPM: P3 (ASCII)

#Generated files (defaults)

gray_from_bmp.pgm

binary_from_bmp.pgm

binary_from_bmp.pbm

Optional ZIP with outputs (and original BMP)

# Limitations

Compressed BMP or JPG/PNG are not parsed here. Convert externally to BMP (BI_RGB) or PPM P3 if needed.

Otsu threshold demo is included in the PPM flow.

# Suggested repo structure
/pure-python-grayscale-binarization/
  ├── notebook_colab.ipynb
  ├── README.md
  └── samples/
      ├── gray_from_bmp.pgm
      ├── binary_from_bmp.pgm
      └── binary_from_bmp.pbm


Tip: To adapt for your own images, upload a BMP (BI_RGB) directly in Colab and reuse the same cells. For non-BMP formats, convert externally (e.g., to BMP or PPM P3) to comply with the “no external libraries” rule.
