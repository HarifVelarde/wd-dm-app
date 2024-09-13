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
    cd python-s3-data-manager
    ```

2. **Install dependencies**:
    ```sh
    pip install -r requirements.txt
    ```

3. **Configure AWS CLI**:
    Ensure your AWS CLI is configured with the necessary permissions to access S3 and ECR.

## Usage

1. **Build the Docker image**:
    ```sh
    docker build -t wd-dm-app .
    ```

2. **Run the Docker container**:
    ```sh
    docker run -e AWS_ACCESS_KEY_ID=your_access_key -e AWS_SECRET_ACCESS_KEY=your_secret_key -e AWS_DEFAULT_REGION=your_region python-s3-data-manager
    ```

3. **Automated Deployment to ECR**:
    The following script automates the process of building the Docker image and pushing it to an ECR repository.

    ```sh
    #!/bin/bash

    # Variables
    AWS_REGION=<YOUR REGION>
    ECR_REPOSITORY=<YOUR REPOSITORY>

    # Authenticate Docker to ECR
    aws ecr get-login-password --region $AWS_REGION | docker login --username AWS --password-stdin $ECR_REPOSITORY

    # Build Docker image
    docker build -t wd-dm-app .

    # Tag Docker image
    docker tag wd-dm-app:latest $ECR_REPOSITORY:latest

    # Push Docker image to ECR
    docker push $ECR_REPOSITORY:latest
    ```

## Contributing

Feel free to submit issues or pull requests. Contributions are welcome!

## License

This project is licensed under the MIT License.
