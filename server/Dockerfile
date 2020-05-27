FROM node:12.16.3-alpine3.10

RUN mkdir -p /home/node/app/node_modules && chown -R node:node /home/node/app
WORKDIR /home/node/app
USER node

COPY --chown=node:node package*.json ./
RUN npm install --only=prod

COPY --chown=node:node ./src ./src

EXPOSE 8080

CMD [ "npm", "start" ]
