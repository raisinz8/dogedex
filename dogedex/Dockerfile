# Stage 1: Build Angular App
FROM node:18 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build --prod

# Stage 2: Serve the App
FROM nginx:alpine
COPY --from=build /app/dist/dogedex /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
