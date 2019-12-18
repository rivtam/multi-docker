FROM node:alpine as builder
WORKDIR /app

COPY package.json .
RUN npm install

COPY . .
RUN npm run build

# the build will be saved in /app/build

# from signifies a start of the next phase / block

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
