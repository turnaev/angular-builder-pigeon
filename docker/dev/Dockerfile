FROM node:18 AS build

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

USER root

RUN apt-get update \
&& DEBIAN_FRONTEND=noninteractive apt-get -y --no-install-recommends install \
 xdg-utils --fix-missing \
&& apt-get clean -y \
&& rm -rf \
 /var/cache/apt/archives \
 /var/lib/apt/lists/* \
 /var/cache/* \
 /usr/share/doc/*

USER node

ENV NPM_CONFIG_PREFIX=/home/node/.npm-global \
PATH=/home/node/.npm-global/bin:/var/www/bin:$PATH \
APP_HOME=/var/www

WORKDIR $APP_HOME

ENV ANGULAR_VERSION=18.0.0

RUN mkdir -p .npm-global \
&& echo 'install angular cli version='$ANGULAR_VERSION \
&& npm install -g @angular/cli@$ANGULAR_VERSION install --loglevel silly \
&& npm install -g  install --loglevel silly

#RUN npm install --loglevel silly \
#&& npm run build

EXPOSE 4200 49153

#CMD ["npm", "start"]
CMD ["sleep", "infinity"]
#"start": "ng serve --host 0.0.0.0 --port 4200 --open --live-reload=true --disable-host-check --public-host http://localhost:4200",
