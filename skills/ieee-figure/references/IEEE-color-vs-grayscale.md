# IEEE Color vs Grayscale Guidance

Verified: 2026-05-27

Sources:
- IEEE Graphics Resolution and Size: https://journals.ieeeauthorcenter.ieee.org/create-your-ieee-journal-article/create-graphics-for-your-article/resolution-and-size/
- IEEE Graphics File Formatting: https://journals.ieeeauthorcenter.ieee.org/create-your-ieee-journal-article/create-graphics-for-your-article/file-formatting/

## Rules of thumb

- Use color when it carries information that cannot be represented clearly by line style, marker shape, direct labels, or panel separation.
- Ensure every color-coded figure remains interpretable in grayscale by adding line styles, marker shapes, annotations, or ordered luminance.
- Use perceptually ordered colormaps such as `cividis` for scalar data unless the venue or field has a stronger convention.
- Use categorical palettes only for unordered classes and keep the number of classes low enough for labels to remain legible.
- Use black-and-white line art at >=600 DPI if raster export is unavoidable.
- Use color or grayscale raster images at >=300 DPI if vector export is not possible.

## Reject during validation

- Scalar data encoded with a rainbow map.
- Decorative gradient backgrounds behind scientific data.
- Legends or labels that become ambiguous when printed in grayscale.
- Text, tick labels, or annotations below 8pt at final size.
