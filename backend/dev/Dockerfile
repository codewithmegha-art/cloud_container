# Uses a slim Python image for a lightweight backend service
FROM python:3.10-slim

# set working directory
WORKDIR /app 

# copies requirements file to the container and installs dependencies
COPY requirements.txt .  
RUN pip install --no-cache-dir -r requirements.txt 

# copies the rest of the application code to the container
COPY . . 


ENV FLASK_APP=app.py
ENV FLASK_ENV=development 

CMD [ "flask" , "run", "--host= 0.0.0", "--port=5000" ] 

