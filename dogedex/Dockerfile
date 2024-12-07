FROM node:20 AS build

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

# RUN ng serve --host 0.0.0.0
RUN npm run build

FROM nginx:alpine

COPY --from=build /app/dist/dogedex /usr/share/nginx/html

COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]