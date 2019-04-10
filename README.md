# Steganography
Python app encrypts a given data (text) into any image so it would be unnoticeable.
[](demo.jpg)

## How does app work?
* Console app includes user menu with 2 option: 
   - use default image (3.000 x 1.995 pixels, .png) and default message (132 KB,  ~23.000 words, ~47 pages of text)
   - use user's image and text
* After source selection app hides a message and saves image to a new file "Coded_img.png"
* If user chooses to decode a message from image, decoded text is saved to a new file "Outpit.txt"

## What is algorithm of hidding?
After a literature research method _Filter First_ was selected as the most effective way to hide message properly.
### To hide the message in original image:
* Canny edge detector is applied to 6 most significant bits (MSB) of image to find areas of the image where there are pixels that are the least like their neighbours. 
* The given message is converted to binary form and is splitted by couples of 2 bits. 
* The maximum size of given message that can be hiden in given image is calculated based on Canny result, user receives notification in case the message is too big or the image is too small.
* If image fits message size, message is hiden in the 2 last significant bits (LSB) of pixels with highest values of the filter first, consistently in each of the layers of image (RGB or grayscale).
* Processed image is saved as a new .png file.

### To find message im image:
* Canny edge detector is applied to 6 most significant bits (MSB) of image.
* 2 LSB are extracted from pixels with highest values of Canny filter.
* All extracted bits are concatenated and converted to ASCII.
* Resulted text is saved as new .txt file. 

## App features
* Code for algorythm implementation is built in the "Python" way: it
   - doesn't contain arithmetic operations
   - works with image and message as np.array
   - contains only binary wise operations
