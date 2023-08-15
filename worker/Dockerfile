from node:14.14.0-alpine
WORKDIR workerapp
COPY package.json .
RUN npm install
COPY . .
CMD ["npm","run","start"]