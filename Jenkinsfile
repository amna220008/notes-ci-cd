FROM nginx:alpine

# Copy Flutter web build output
COPY build/web /usr/share/nginx/html

# Expose web port
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
