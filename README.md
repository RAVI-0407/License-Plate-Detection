# Workshop-5 - License Plate Detection Using OpenCV and Haar Cascade Classifier
## AIM

To develop a Python-based license plate detection system using OpenCV and a Haar Cascade Classifier to detect and highlight the license plate region in a vehicle image.

## REQUIREMENTS
Python 3.x
OpenCV
Haar Cascade XML classifier
Vehicle image

## PROCEDURE
1. Install Python and OpenCV.
2. Download haarcascade_russian_plate_number.xml.
3. Place the XML file in the same directory as the Python program.
4. Place a vehicle image such as car.jpg in the project directory.
5. Import the OpenCV library.
6. Load the Haar Cascade classifier.
7. Read the input vehicle image.
8. Convert the image from BGR to grayscale.
9. Apply the Haar Cascade classifier to detect license plates.
10. Draw a rectangle around each detected license plate.
11. Crop and display the detected plate region.
12. Display the final image containing the detected license plate.
13. Press any key to close the output windows.

## PROGRAM
```
import cv2

# Load Haar Cascade Classifier
plate_cascade = cv2.CascadeClassifier("haarcascade_russian_plate_number.xml")

# Read input image
image = cv2.imread("carnp.jpg")

if image is None:
    print("Error: Could not read the image.")
    exit()

# Convert image to grayscale
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Detect license plates
plates = plate_cascade.detectMultiScale(
    gray,
    scaleFactor=1.1,
    minNeighbors=5,
    minSize=(30, 30)
)

# Draw rectangles around detected plates
for (x, y, w, h) in plates:
    cv2.rectangle(
        image,
        (x, y),
        (x + w, y + h),
        (0, 255, 0),
        2
    )

    # Crop the detected plate
    plate = image[y:y + h, x:x + w]

    # Display the cropped plate
    cv2.imshow("License Plate", plate)

print("Number of plates detected:", len(plates))

# Display result
cv2.imshow("License Plate Detection", image)

cv2.waitKey(0)
cv2.destroyAllWindows()
```

## Output


<img width="768" height="438" alt="image" src="https://github.com/user-attachments/assets/471cda83-bc7c-49b9-8871-fe2776f97e14" />

---

<img width="195" height="65" alt="image" src="https://github.com/user-attachments/assets/8b2a0f65-efb9-4620-a485-4a76197114dd" />

## Result
The vehicle image was successfully processed using OpenCV and the Haar Cascade Classifier. The license plate was detected and highlighted with a rectangular bounding box. The detected license plate region was also cropped and saved as an image.
