# Node Application Deployment using Podman

This guide will help you deploy a simple Node.js application using Podman.

## Step 1: Clone the Repository

Open your terminal and run:

```bash
git clone https://github.com/rat9615/simple-nodejs-app.git 
cd simple-nodejs-app
Step 2: Install Dependencies
Check if you have Node.js and npm installed:

node -v 
npm -v
Once you have Node.js and npm installed, install the project dependencies:

Step 3: Create Dockerfile
Create a file named Dockerfile in the root of your project directory with the following content:
FROM node
WORKDIR /app

# Copy package.json and package-lock.json first for better caching
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Expose the port the app runs on
EXPOSE 3000

# Define the command to run the application
ENTRYPOINT ["npm", "start"]

Step 4: Build the Docker Image
Build the Docker image using the following command:

podman build -t simple-nodejs-app .

Step 5: Run the Podman Container
Run the Podman container with the following command:

podman run -d -p 3000:3000 --name my-node-app simple-nodejs-app

Step 6: Access the Application
You can access the application by navigating to the following URL in your web browser:

http://localhost:3000
