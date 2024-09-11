# Use an official Nginx image as the base image
FROM nginx:alpine

RUN rm /usr/share/nginx/html/index.html

COPY . /usr/share/nginx/html/

WORKDIR /app

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

