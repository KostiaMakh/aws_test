# the base image to run your application
FROM python:3.8.10-slim

# setup environment variable
ENV DockerHOME=/home/app/webapp

# set work directory
RUN mkdir -p $DockerHOME

# where your code lives
WORKDIR $DockerHOME

# set environment variables

# this ensures that the Python interpreter doesn’t generate .pyc files, we don't need them
ENV PYTHONDONTWRITEBYTECODE 1
# this will send python output straight to the terminal(standard output) without being buffered
ENV PYTHONUNBUFFERED 1

# install dependencies
RUN pip install --upgrade pip

# copy the whole project to your docker home directory.
COPY . $DockerHOME
# run this command to install all dependencies
RUN pip install -r requirements.txt
# port where the Django app runs
EXPOSE 5000
# start the server on port 5000, this is what EB listens for
CMD ["python", "manage.py", "runserver", "0.0.0.0:5000"]