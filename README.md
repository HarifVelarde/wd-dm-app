# Python S3 Data Manager

This application is written in Python and is designed to manage data in an Amazon S3 bucket. The application runs inside a Docker container, and the Docker image is automatically pushed to an Amazon ECR repository.

## Features

- **Data Management**: Perform CRUD operations on data stored in an S3 bucket.
- **Dockerized**: The application runs inside a Docker container for easy deployment.
- **Automated Deployment**: The Docker image is automatically built and pushed to an Amazon ECR repository.

## Prerequisites

- Python 3.x
- Docker
- AWS CLI configured with appropriate permissions

## Setup

1. **Clone the repository**:
    ```sh
    git clone https://github.com/yourusername/wd-dm-app.git
    cd wd-dm-app
    ```

2. **Install dependencies**:
    ```sh
    pip install -r requirements.txt
    ```

3. **Configure AWS CLI**:
    Ensure your AWS CLI is configured with the necessary permissions to access S3 and ECR.

## How works django-storages library

Django-storages is a collection of custom storage backends for Django.

- settings.py file
```sh
    STORAGES = {
        # Media file (image) management   
        "default": {
            "BACKEND": "storages.backends.s3boto3.S3StaticStorage",
        },
        # CSS and JS file management
        "staticfiles": {
            "BACKEND": "storages.backends.s3boto3.S3StaticStorage",
        },
    }
```

## STORAGES Dictionary:

- Media files:
  The default key specifies that media files (like images) will be handled by the S3StaticStorage backend, which means they'll be uploaded to the S3 bucket.
- Static files:
  The staticfiles key specifies that static files (CSS and JS) will also be handled by the S3StaticStorage backend, which means they will be served from the S3 bucket.

## Creating a RP:


To make any changes to the code, you will first need to create a new branch. After completing your changes, create a pull request in the repository. Once the pull request is submitted, a script will automatically trigger the creation of a new Docker image, which will be stored in an Amazon ECR (Elastic Container Registry) repository. After the image is successfully built and stored, it will be deployed to an EC2 instance.

## Use

1. **Login:
    ```sh
    Access to the application using this link -> http://18.236.130.151:8000/admin/login/?next=/admin/

    user: harif
    pass: odin666
    ```

2. **Site Administration**:
    ```sh
    Under the CRM menu choose the profiles option and choose Profile object
    ```
3. **Change profile picture:

    ```sh
    Choose a new image file, this will be used as profile picture. This image will be stored on a S3 bucket.
    You can change the picture using the button clear and chose a new one.
    ```


