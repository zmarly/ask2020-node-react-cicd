FROM node:12.16.3-alpine3.10 as builder
WORKDIR /home/node/app
COPY package*.json ./
RUN npm install
COPY ./ ./

RUN npm run build

FROM nginx:1.17.10-alpine
COPY --from=builder /home/node/app/build /usr/share/nginx/html
COPY --from=builder /home/node/app/nginx.conf /etc/nginx/nginx.conf

EXPOSE 80

ENTRYPOINT [ "nginx", "-g", "daemon off;" ]
