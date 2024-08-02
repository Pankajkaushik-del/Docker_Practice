# Use an official Ubuntu base image
FROM ubuntu

# Set the working directory inside the container
WORKDIR /app

# Copy the requirements file and application directory to the container
COPY requirements.txt /app
COPY devops /app

# Update and install Python and pip, and create a virtual environment
RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv && \
    python3 -m venv venv && \
    . venv/bin/activate && \
    pip install --upgrade pip && \
    pip install -r requirements.txt && \
    cd devops

ENTRYPOINT ["python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]




