FROM node:22

WORKDIR /backend-app
COPY package.json ./
RUN npm install
COPY .env ./
COPY index.js ./

EXPOSE 5050

CMD [ "npm", "start" ]