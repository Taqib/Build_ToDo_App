# Use the official Node.js 16 image as the base image
FROM node:16

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy the package.json and package-lock.json files to the working directory
COPY package*.json ./

# Install the dependencies
RUN npm install

# Copy the rest of the application code to the working directory
COPY . .

# Expose the port that the API Gateway will be running on
EXPOSE 5000

# Define the environment variable for the PORT
ENV PORT=5000

# Command to run the API Gateway
CMD ["npm", "start"]
