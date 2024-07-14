# Use an official Python runtime as a parent image
FROM python:3.11-slim

# Set environment variables
ENV DB_USERNAME=myuser
ENV DB_PASSWORD=${POSTGRES_PASSWORD}
ENV DB_HOST=host.docker.internal
ENV DB_PORT=5433
ENV DB_NAME=mydatabase
ENV APP_PORT=5153

# Set the working directory in the container
WORKDIR /app

# Install curl and other needed packages
RUN apt-get update && apt-get install -y curl

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in requirements.txt
RUN pip install --upgrade pip setuptools wheel && \
    pip install -r requirements.txt

# Make port available to the world outside this container
EXPOSE ${APP_PORT}

# Run app.py when the container launches
CMD ["python", "app.py"]
