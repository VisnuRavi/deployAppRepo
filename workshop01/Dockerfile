FROM python:3.11-slim

# Set working directory inside the container
WORKDIR /app

# Copy only the folder from repo into container
COPY workshop01/ .  

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Expose port
EXPOSE 5000

# Run Flask
ENV FLASK_APP=app.py
ENV FLASK_RUN_HOST=0.0.0.0
CMD ["flask", "run"]
