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

# Install correct torch torchaudio torchvision
RUN pip install --no-cache-dir torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

# Expose the port Streamlit will run on
EXPOSE 8501

# Define environment variable to ensure that Python outputs are sent straight to terminal without being buffered
ENV PYTHONUNBUFFERED=1

# Set the default command to execute when creating a new container
CMD ["python", "-m", "riffusion.streamlit.playground"]