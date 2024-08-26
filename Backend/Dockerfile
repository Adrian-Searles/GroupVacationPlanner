FROM nginx:1.13
COPY conf /etc/nginx/conf.d/default.conf
FROM python:3.9-slim-buster

WORKDIR /backend

# Copy requirements and install dependencies
COPY requirements.txt /backend/
RUN pip3 install --no-cache-dir -r requirements.txt


# Install additional dependencies
RUN pip3 install requests pipenv psycopg2-binary


# Copy application code
COPY . /backend/

# RUN apt-get update && apt-get install -y netcat

# Set environment variables
ENV FLASK_APP=app
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# RUN pipenv install sqlalchemy psycopg2-binary

EXPOSE 5000
# CMD ["nginx", "-c", "./nginx/conf"]

# run entrypoint.sh
ENTRYPOINT ["./entrypoint.sh"]

# Default command to start Flask
CMD ["python3", "manage.py", "run", "--host=0.0.0.0"]

