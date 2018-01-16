FROM node:latest as builder

ADD package.json .
ADD yarn.lock .
ADD src/ src/
RUN yarn install && yarn run build

FROM nginx:latest as runner

RUN mkdir /wwwroot
COPY --from=builder ./build /wwwroot
COPY ./nginx.conf /etc/nginx/nginx.conf
EXPOSE 8080

RUN service nginx start
