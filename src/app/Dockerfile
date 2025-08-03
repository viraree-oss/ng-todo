# Stage 1: Build the Angular application
FROM node:alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build -- --configuration production

# Stage 2: Serve the Angular application with Nginx
FROM nginx:alpine
COPY --from=build /app/dist/book-survey /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
