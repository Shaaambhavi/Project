# Start from official Python image
FROM python:3.10-slim

# Install system packages (including Tesseract OCR)
RUN apt-get update && \
    apt-get install -y tesseract-ocr libglib2.0-0 libsm6 libxrender1 libxext6 && \
    apt-get clean

# Set the working directory
WORKDIR /app

# Copy all files from your local project into the image
COPY . /app

# Install Python packages
RUN pip install --no-cache-dir -r requirements.txt

# Expose the port (optional but good practice)
EXPOSE 10000

# Start your app using Gunicorn (recommended for production)
CMD ["gunicorn", "app:app", "--bind", "0.0.0.0:10000"]
