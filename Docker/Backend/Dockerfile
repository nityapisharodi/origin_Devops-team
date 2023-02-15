FROM node:18-alpine

# Use this path as the default location for all subsequent commands
WORKDIR /app

# Copy package.json and package-lock.json files into our image before run "npm install".
#COPY package*.json .
COPY ./backend .

# Download/install dependencies in "node_modules" folder.
RUN npm install
#RUN npm install && npm cache clean --force

#Copy source code to image
#COPY . .

# Define webserver port
EXPOSE 3000

# Start webserver
CMD ["npm", "run", "dev"]