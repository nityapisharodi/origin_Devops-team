FROM node:18-alpine as appbuild
# Use this path as the default location for all subsequent commands
WORKDIR /app
# Copy package.json and package-lock.json files into our image before run "npm install".
#COPY package*.json .
COPY ./frontend .
# Download/install dependencies in "node_modules" folder.
RUN npm ci
RUN npm run build
#Production with nginx
FROM nginx:1.23.3-alpine
# Define webserver port
COPY --from=appbuild /app/build /usr/share/nginx/html
COPY ./Docker/Frontend/Nginx/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
# Start webserver
CMD ["nginx", "-g", "daemon off;"]
