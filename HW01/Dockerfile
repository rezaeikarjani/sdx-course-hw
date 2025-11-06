# 1. Use an official Python runtime as a parent image
FROM python:3.9-slim

# 2. Set the working directory in the container
WORKDIR /app

# 3. Copy the requirements file first to leverage Docker cache
COPY requirements.txt .

# 4. Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# 5. Copy the application script and its data files
COPY feeder.py .
COPY toyota_data.csv .
COPY ca.crt .         

# 6. Run feeder.py when the container launches
CMD ["python", "feeder.py"]
