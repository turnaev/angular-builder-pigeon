FROM local/angular-builder AS build

COPY . /var/www

USER root

RUN npm install \
 && ng build

FROM nginx

COPY --from=build /var/www/dist/pigeon/browser /var/www

COPY ./docker/prod/nginx/conf.d /etc/nginx/conf.d
