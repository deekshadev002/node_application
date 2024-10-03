Node Application Deploy using Podman 
======================================================================

Step 1. Clone the Repository
Open your terminal and run:
git clone https://github.com/rat9615/simple-nodejs-app.git 
cd simple-nodejs-app



Step 2. Install Dependencies



node -v 
npm -v

Once you have Node.js and npm installed, install the project dependencies:
npm install


Step 3. Create  Dockerfile
=================================================================
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

======================================================================





Step 4. Build the Docker Image:
podman build -t simple-nodejs-app .


Step 5. Run the Podman Container:
podman run -d -p 3000:3000 --name my-node-app simple-nodejs-app








Step 6: Access the Application
http://localhost:3000




