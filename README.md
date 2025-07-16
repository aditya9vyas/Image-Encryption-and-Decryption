# Image-Encryption-and-Decryption
Image Encryption and Decryption with PIL (Python Imaging Library) Module in Python Script

Prerequisites
Python 3.x
PIL (Python Imaging Library) is installed (0pip install Pillow)

How to Use

1. Encryption
To encrypt an image, use the encrypt_image function with the path to your original image file:
from PIL import Image
import os

# Encryption function
def encrypt_image(image_path):
    img = Image.open(image_path)
    pixels = img.load()
    width, height = img.size

    for y in range(height):
        for x in range(width):
            r, g, b = pixels[x, y]
            # Example encryption: invert each pixel's color
            pixels[x, y] = (255 - r, 255 - g, 255 - b)

    encrypted_image_path = os.path.join(os.path.dirname(image_path), "encrypted_" + os.path.basename(image_path))
    img.save(encrypted_image_path)
    print("Image encrypted successfully.")
    return encrypted_image_path

# Example usage
original_image_path = "path_to_your_original_image.jpg"
encrypted_image_path = encrypt_image(original_image_path)

2. Decryption
To decrypt the encrypted image back to its original form, use the decrypt_image function with the path to the encrypted image file :

# Decryption function
def decrypt_image(encrypted_image_path):
    encrypted_img = Image.open(encrypted_image_path)
    pixels = encrypted_img.load()
    width, height = encrypted_img.size

    for y in range(height):
        for x in range(width):
            r, g, b = pixels[x, y]
            # Reverse the encryption: invert each pixel's color
            pixels[x, y] = (255 - r, 255 - g, 255 - b)

    decrypted_image_path = os.path.join(os.path.dirname(encrypted_image_path), "decrypted_" + os.path.basename(encrypted_image_path)[len("encrypted_"):])
    encrypted_img.save(decrypted_image_path)
    print("Image decrypted successfully.")
    return decrypted_image_path

# Example usage
decrypted_image_path = decrypt_image(encrypted_image_path)

3. Notes
The encryption and decryption process demonstrated here is a simple example ((255 - r, 255 - g, 255 - b)). You can modify the encryption logic for stronger security as per your requirements.

Ensure that the paths provided (original_image_path, encrypted_image_path) are valid paths to existing image files.
