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
    python app.py
    ```

5. Send a POST request to the `/detect` endpoint with an image file in the request body. You can use tools such as Postman or cURL to send requests.

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

## Dependencies

- Flask
- OpenCV

## Models

- `haarcascade_frontalface_default.xml`: Cascade classifier for face detection.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
