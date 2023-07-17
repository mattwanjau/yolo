
FROM node:14-alpine

# Set the working directory to /client
WORKDIR /client

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the 
COPY . .

# Expose the port the client will listen on
EXPOSE 3000

# Start the client
CMD ["npm", "start"]