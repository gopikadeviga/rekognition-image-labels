# Image Labels Generator using Amazon Rekognition

A Python command-line tool that detects objects, scenes, and concepts in an image stored in Amazon S3 using Amazon Rekognition. It prints each detected label with its confidence score and opens a window showing the image with labelled bounding boxes around the detected objects.

# How it works

-An image is uploaded to an Amazon S3 bucket.
-A local Python script, authenticated through an IAM user configured with the AWS CLI, calls Rekognition's detect_labels API on that image.
-Rekognition returns the labels with confidence scores, which the script prints to the console.
-The script downloads the image and draws a labelled bounding box (name and confidence) around each detected object, then displays it.

## AWS Services Used

| Service | Role in this project |
| --- | --- |
| Amazon S3 | Stores the input image |
| Amazon Rekognition | Performs label detection (managed computer vision) |
| AWS IAM | Provides programmatic credentials with least-privilege access |
| AWS CLI | Configures local credentials used by the SDK |

## Rekognition labels detected output

<img width="925" height="662" alt="0 2 rekognition_detected_output" src="https://github.com/user-attachments/assets/927e7493-7cac-4311-a007-a01a143d0f41" />
