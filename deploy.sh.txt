#!/bin/bash

CONTAINER_NAME=devops-container
IMAGE_NAME=devops-app

echo "Stopping old container..."
docker stop $CONTAINER_NAME || true
docker rm $CONTAINER_NAME || true

echo "Building new image..."
docker build -t $IMAGE_NAME .

echo "Starting container..."
docker run -d --name $CONTAINER_NAME $IMAGE_NAME

echo "Deployment completed"