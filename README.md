# Image Labels Generator using Amazon Rekognition

A Python command-line tool that detects objects, scenes, and concepts in an image stored in Amazon S3 using Amazon Rekognition. It prints each detected label with its confidence score and opens a window showing the image with labelled bounding boxes around the detected objects.

# How it works

1. An image is uploaded to an Amazon S3 bucket.
2. A local Python script, authenticated through an IAM user configured with the AWS CLI, calls Rekognition's detect_labels API on that image.
3. Rekognition returns the labels with confidence scores, which the script prints to the console.
4. The script downloads the image and draws a labelled bounding box (name and confidence) around each detected object, then displays it.


## AWS Services Used

| Service | Role in this project |
| --- | --- |
| Amazon S3 | Stores the input image |
| Amazon Rekognition | Performs label detection (managed computer vision) |
| AWS IAM | Provides programmatic credentials with least-privilege access |
| AWS CLI | Configures local credentials used by the SDK(boto 3) |

# Requirements

- Python 3.9 or later
- An AWS account and an IAM user with programmatic access
- The AWS CLI installed and configured

> Note : The S3 bucket and the Rekognition call must be in the **same AWS region**.

## IAM Permissions

The IAM user is given the least privilage, only two permissions required:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "rekognition:DetectLabels",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::YOUR_BUCKET_NAME/*"
    }
  ]
}
```

## Rekognition labels detected output

<img width="925" height="662" alt="0 2 rekognition_detected_output" src="https://github.com/user-attachments/assets/927e7493-7cac-4311-a007-a01a143d0f41" />

### Example output

```
Detected 10 label(s) for 'street.jpg':
  City                      100.00%
  Metropolis                100.00%
  Urban                     100.00%
  Road                      100.00%
  Street                    100.00%
  Neighborhood               99.99%
  Intersection               99.64%
  Car                        99.45%
  Person                     98.40%
  Cityscape                  98.24%
```
