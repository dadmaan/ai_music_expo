# Use an official PyTorch runtime as a parent image, with GPU support
FROM pytorch/pytorch:2.0.1-cuda11.7-cudnn8-runtime

# Change the working directory to the cloned repository
WORKDIR /usr/src/app/riffusion

# Install ffmpeg
RUN apt-get update && \
    apt-get install -y ffmpeg && \
    rm -rf /var/lib/apt/lists/*

# Copy the requirements text into the container
COPY requirements.txt ./

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Expose the port Streamlit will run on
EXPOSE 8501

# Set the default command to execute when creating a new container
CMD ["python", "-m", "riffusion.streamlit.playground"]