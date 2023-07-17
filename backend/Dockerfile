
FROM node:13-alpine
# Set the working directory to /backend
WORKDIR /backend

# Copy package.json and package-lock.json to the working directory
COPY package.json .

# Install app dependencies
RUN npm install

# Copy the rest of the backend source code to the working directory
COPY . .

# Expose the port the app will listen on
EXPOSE 5000

# Start the app
CMD ["npm", "start"]