#first step
FROM node:alpine as builder
WORKDIR '/APP'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

#second step
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html