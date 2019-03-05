# Use an existing Docker image as a base
FROM node:alpine

# Specify the directory to which our files will be copied
WORKDIR /usr/app

# Copy the package.json to the invoked container (to make npm install run only if package.json changes)
COPY ./package.json ./

# Download and install dependencies
RUN npm install

# Copy all the file to the invoked container
COPY ./ ./

# Tell the image what to do when it starts a container
CMD ["npm", "start"]