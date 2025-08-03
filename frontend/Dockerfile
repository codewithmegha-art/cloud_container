# set the base images for the frontend service
FROM node:18-slim
 
# set thw working directory inside the container 
WORKDIR /app  

# copt the package.json and package-lock.json files to the container 
COPY package*.json . 
RUN npm install   

# copy the rest of the application code to the container 
COPY . .  

CMD ["npm" , "start"] 




