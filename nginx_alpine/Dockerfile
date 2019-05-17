FROM nginx:1.15-alpine

RUN apk upgrade --update \
&& apk add composer curl && \
apk add --no-cache freetype libpng libjpeg-turbo freetype-dev libpng-dev libjpeg-turbo-dev

EXPOSE 80

ENV PHP_SERVICE_URL localhost
ENV PHP_SERVICE_PORT 9000

CMD ["nginx", "-g", "daemon off;"]
