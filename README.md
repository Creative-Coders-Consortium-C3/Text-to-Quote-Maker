# Text to Quote Maker Documentation

## Overview

Text to Quote Maker is a Python project that generates quote images from text input. It offers two main functionalities:
1. Text to quote without border
2. Text to quote with border

The project is designed to work with Hindi text and supports various customization options.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1Xkq1uH_VnZa34ee7LZbdTM2F6cBYc-ZD?usp=sharing)

## Features

- Read quotes from Excel files
- Support for Hindi text
- Customizable background images
- Dynamic font scaling
- Image effects (sepia, grayscale)
- Watermarking
- Border options (for the version with border)
- Concurrent processing for faster generation

## Requirements

The project requires the following Python libraries:
- pandas
- numpy
- opencv-python (cv2)
- Pillow (PIL)
- matplotlib
- numba

These can be installed using pip:

```bash
!pip install pandas pillow opencv-python matplotlib numba
!pip install --upgrade pillow
!pip install --upgrade pandas
```

## Usage Instructions

1. Open the provided Google Colab notebook.
2. Run the installation cell to install required libraries.
3. Choose between "Text to quote without border" or "Text to quote with border" by running the corresponding cell.
4. Follow the prompts to upload necessary files and set parameters.

### File Uploads

You'll be prompted to upload three files:
1. Excel file containing quotes
2. Background image
3. Font file (must support Hindi)

### Parameter Customization

#### Common Parameters

- **Column name**: Name of the column in the Excel file containing quotes (default is 'Quote').
- **Bottom margin percentage**: Percentage of image height for the bottom text area (e.g., 0.2 for 20%).

#### Additional Parameters for Version with Border

- **Border size**: Size of the border in pixels.
- **Border color**: Choose between white, black, or custom RGB values.

### Output

The script generates quote images and saves them in a 'quote_images' folder. This folder is then zipped and downloaded automatically.

## Customization Guide

### Image Size

The background image is resized to 1000x1000 pixels. To change this, modify the `resize_image` function call in `generate_quote_image`:

```python
background = resize_image(background, new_width, new_height)
```

### Font Size

Font size is dynamically calculated, but you can adjust the range by modifying `max_font_size` and `min_font_size` in `get_optimal_font_scale`:

```python
def get_optimal_font_scale(..., max_font_size=45, min_font_size=17, ...):
```

### Text Color

To change the text color, modify the `text_color` parameter in `add_text_to_image`:

```python
image_with_quote = add_text_to_image(..., text_color=(255, 255, 255), ...)
```

### Image Effects

The script randomly applies 'none', 'sepia', or 'grayscale' effects. To change this, modify the `image_effect` assignment in `process_quote`:

```python
image_effect = np.random.choice(['none', 'sepia', 'grayscale'])
```

### Watermark

To modify the watermark, change the text in `generate_quote_image`:

```python
final_image = add_watermark(image_with_effect, "Your Watermark Text", watermark_font)
```

## Troubleshooting

- If you encounter encoding issues with the Excel file, try specifying the encoding explicitly in `read_quotes_from_excel`.
- For font compatibility issues, ensure your font file supports Hindi characters.
- If images are not generating correctly, check the log file for detailed error messages.

## Contributing

To contribute to this project:
1. Fork the repository
2. Create a new branch for your feature
3. Commit your changes
4. Push to the branch
5. Create a new Pull Request

## License

This project is open-source and available under the MIT License.
