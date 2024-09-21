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

# Expose the port that the ToDo service will be running on
EXPOSE 8000

# Define the environment variable for the PORT
ENV PORT=8000

# Command to run the ToDo service
CMD ["node", "index.js"]
