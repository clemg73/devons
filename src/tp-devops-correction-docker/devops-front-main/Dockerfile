FROM node:12.16.3-stretch-slim AS build

COPY src/ /opt/front/src/
COPY public/ /opt/front/public/
COPY package.json /opt/front
COPY yarn.lock /opt/front/
COPY default.conf /opt/front/
COPY .env.production /opt/front/

WORKDIR /opt/front

RUN npm install
RUN npm run build

FROM nginx:1.15.7-alpine

COPY --from=build /opt/front/dist /usr/share/nginx/html/
COPY --from=build /opt/front/default.conf /etc/nginx/conf.d/default.conf