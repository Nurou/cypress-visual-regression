# base image
FROM cypress/browsers:node16.16.0-chrome107-ff107

# set variables
ARG CYPRESS_VERSION=12.7.0
ENV SNAPSHOT_DIRECTORY /usr/src/app/cypress/snapshots
ENV CI true
RUN echo ${CYPRESS_VERSION}

# set working directory
WORKDIR /usr/src/app

# install cypress, and cypress-visual-regression
COPY package.json /usr/src/app/package.json
RUN npm install cypress@${CYPRESS_VERSION}
RUN npm install

# copy cypress files and folders
COPY cypress /usr/src/app/cypress
COPY cypress.config.js /usr/src/app/cypress.config.js
COPY web /usr/src/app/web

# copy dist
COPY dist /usr/src/app/dist

# confirm the cypress install
RUN ./node_modules/.bin/cypress verify
