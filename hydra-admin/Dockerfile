FROM node:12.7-alpine as build-stage

WORKDIR /app
ARG configuration=production
COPY . /app
RUN npm install

RUN npm run build -- --output-path=./dist/out --configuration $configuration

FROM nginx

COPY --from=build-stage /app/dist/out/ /usr/share/nginx/html
# COPY ./nginx-custom.conf /etc/nginx/conf.d/default.conf