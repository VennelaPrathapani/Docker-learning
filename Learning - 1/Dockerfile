FROM ubuntu:latest

# Set the working directory in the image
WORKDIR /app

# Copy the files from Host file system to the image file system
COPY . /app

# Install the neccessary packages
RUN apt-get update && apt-get install -y python3 python3-pip

#Set environment variables
ENV NAME World

# run a command to start the application
CMD ["python3" , "app.py"]