# Base image with Python
FROM python:3.8-slim

# Set working directory
WORKDIR /app

# Copy requirements (if you have any)
COPY requirements.txt .

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy application files
COPY main.py .
COPY diabetes_model.sav .

# Expose port
EXPOSE 8000

# Command to run the app
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]