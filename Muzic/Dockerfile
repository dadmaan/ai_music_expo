# Use an official PyTorch runtime as a parent image, with GPU support
FROM pytorch/pytorch:1.7.1-cuda11.0-cudnn8-runtime

# Set the working directory in the container
WORKDIR /usr/src/app/muzic

# Install system dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    python3.6 \
    python3.6-dev \
    python3-pip \
    python3-setuptools \
    git \
    ffmpeg \
    libsndfile1 \
    pkg-config libblas-dev liblapack-dev gfortran libssl-dev libsasl2-dev \
    libxml2-dev libxslt1-dev zlib1g-dev libldap2-dev libffi-dev libmysqlclient-dev libjpeg-dev libpq-dev libjpeg8-dev liblcms2-dev libatlas-base-dev && \
    rm -rf /var/lib/apt/lists/*

# Copy the requirements text into the container
COPY requirements.txt ./

# Install Python packages
RUN pip3 install --upgrade pip
RUN pip install --no-cache-dir -r requirements.txt

# Install Jupyter Notebook
RUN pip install notebook

# Make ports 8888 7861 available to the world outside this container
EXPOSE 8888 7861

# Define environment variable to ensure that Python outputs are sent straight to terminal without being buffered
ENV PYTHONUNBUFFERED=1

# Set the default command to execute when creating a new container
# This command starts the Jupyter Notebook server
CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--allow-root", "--NotebookApp.token=''", "--NotebookApp.password=''"]

