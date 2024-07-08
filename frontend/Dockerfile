FROM node:18

WORKDIR /app

# Set npm to use HTTPS
RUN npm config set registry https://registry.npmjs.org/

# Use HTTPS instead of git protocol
RUN git config --global url."https://".insteadOf git://

# Copy package files
COPY package*.json ./

# Clear npm cache and install dependencies
RUN npm cache clean --force && npm install

# Copy the rest of the application code
COPY . .

# Build the React app
RUN npm run build

# Install a simple HTTP server to serve static content
RUN npm install -g serve

# Expose the port the app runs on
EXPOSE 3000

# Define the command to run the app
CMD ["serve", "-s", "build", "-l", "3000"]