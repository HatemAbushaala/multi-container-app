# Phase 1
FROM node:16-alpine as builder

WORKDIR productionapp
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

# Phase 2
FROM nginx as runner

# this will be used by esb to map ports
EXPOSE 3000
# copy cusom nginx config file
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# copy builder phase build results to nginx folder
COPY --from=builder /productionapp/build /usr/share/nginx/html

# nginx will start by default we don't need to specify start command