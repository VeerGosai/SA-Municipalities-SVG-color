# Python Script: Update SVG with Municipality Colors

This Python script updates the fill color of municipalities in an SVG map of South Africa based on custom color codes.

## Requirements:
- Python 3.x
- `xml.etree.ElementTree` (standard library)

## Script:

```python
import xml.etree.ElementTree as ET

# Define custom colors for municipalities
province_colors = {
    'BUF': '#FF0000', 'CPT': '#FF0000', 'EC101': '#FF0000',  # Example entries
    'LIM343': '#00FF00',  # Example for different color
}

svg_file_path = 'path_to_svg_file.svg'
updated_svg_file_path = 'path_to_updated_svg_file.svg'

# Parse SVG
tree = ET.parse(svg_file_path)
root = tree.getroot()

# Update colors for municipalities
for province_id, color in province_colors.items():
    for elem in root.findall(f".//*[@id='{province_id}']"):
        elem.set('style', f'fill:{color}')

# Save updated SVG
tree.write(updated_svg_file_path)
print(f"Updated SVG saved to: {updated_svg_file_path}")
