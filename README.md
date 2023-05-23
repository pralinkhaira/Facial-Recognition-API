# Facial Recognition API

This API allows users to upload images and receive facial recognition results, including bounding boxes around detected faces and corresponding labels.

## Getting Started

1. Clone the repository to your local machine.

2. Install the required dependencies using pip:

    ```
    pip install -r requirements.txt
    ```

3. Download the `haarcascade_frontalface_default.xml` file from the OpenCV GitHub repository and place it in the `models/` directory.

4. Run the Flask server:

    ```
    python face_recognition.py test.jpg haarcascade_frontalface_default.xml
    ```

5. Send a POST request to the `/detect` endpoint with an image file in the request body. You can use tools such as Postman or cURL to send requests.

    - If using Postman:
        1. Open Postman and create a new request.
        2. Select `POST` as the HTTP method.
        3. Enter `http://localhost:5000/detect` as the request URL.
        4. Select the `Body` tab.
        5. Select `form-data` as the request body type.
        6. Add a new key-value pair to the request body, where the key is `file` and the value is the path to the image file.
        7. Click `Send`.

    - If using cURL:
        ```
        curl -X POST -F 'file=@path/to/image.jpg' http://localhost:5000/detect
        ```

6. Receive the facial recognition results in JSON format, including the number of detected faces, the coordinates of the bounding boxes, and the corresponding labels.

## API Endpoints

### `/detect`

#### POST

Detect faces in an uploaded image.

**Request:**

- `file`: The image file to upload.

**Response:**

```
{
  "num_faces": 2,
  "faces": [
    {
      "x": 100,
      "y": 150,
      "width": 200,
      "height": 200,
      "label": "John Doe"
    },
    {
      "x": 400,
      "y": 200,
      "width": 150,
      "height": 150,
      "label": "Jane Doe"
    }
  ]
}
```

The response contains the following fields:

- `num_faces`: The number of detected faces in the uploaded image.
- `faces`: An array of face objects, each containing the following fields:
    - `x`: The x-coordinate of the top-left corner of the bounding box around the face.
    - `y`: The y-coordinate of the top-left corner of the bounding box around the face.
    - `width`: The width of the bounding box around the face.
    - `height`: The height of the bounding box around the face.
    - `label`: The label or name associated with the detected face.

## Dependencies

- Flask
- OpenCV

## Models

- `haarcascade_frontalface_default.xml`: Cascade classifier for face detection.

## Update Info

Version 1.1 (Updated May 2023)

- Implemented error handling mechanisms to gracefully handle exceptions during execution.
- Added input validation to ensure that the image file and cascade classifier file exist.
- Improved code modularity by separating the face detection logic from file handling and display logic.
- Implemented command-line arguments for specifying the image file and cascade classifier file.
- Added performance optimization techniques, such as reducing image size and exploring more efficient algorithms.
- Extended the code to handle multiple faces by detecting and drawing bounding boxes around all faces.
- Tuned parameters, such as scaleFactor and minNeighbors, to improve face detection accuracy.
- Improved user interface by exploring options for a more user-friendly graphical user interface (GUI).
- Modified the code to perform real-time face detection using a webcam or video stream.


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
