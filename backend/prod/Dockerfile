# using a slim version of Python 3.10 as the base image
FROM python:3.10-slim   

# set the working directory inside the container
WORKDIR /app  

# copy the requirements file into the container and install dependencies 
COPY requirements.txt . 
RUN pip install --no-cache-dir -r requirements.txt  

# copy the rest of the application code into the container
COPY . . 

ENV FLASK_APP=app.py 
ENV FLASK_ENV=production  
 
CMD ["flask", "run", "--host=0.0.0", "--port=50001"]  








