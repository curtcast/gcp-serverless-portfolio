# Step 1: Use the official lightweight Nginx image
FROM nginx:alpine

# Step 2: Copy your custom Nginx configuration to the container
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Step 3: Copy all your website files (HTML, CSS, JS, images) into the Nginx public folder
COPY . /usr/share/nginx/html/

# Step 4: Expose port 8080 for Cloud Run
EXPOSE 8080

# Step 5: Start Nginx and keep it running in the foreground
CMD ["nginx", "-g", "daemon off;"]
