# Use an official Python runtime as a parent image
FROM python:3.7.3-alpine
	
RUN apk  --no-cache add build-base
RUN apk  --no-cache add postgresql-dev

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

RUN apk add --no-cache --virtual .build-deps \
    ca-certificates gcc postgresql-dev linux-headers musl-dev \
    libffi-dev jpeg-dev zlib-dev \
    && pip install --no-cache -r requirements.txt


EXPOSE 9500
# Run app.py when the container launches
CMD ["gunicorn" , "-b", "0.0.0.0:9500", "app:app"]

