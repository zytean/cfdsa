## Set base docker image
FROM node:latest

## Set enviroment variable
ENV APP_ROOT=/app
ENV APP_PORT=3000
ENV DB_HOST=localhost
ENV DB_USER=root
ENV DB_PASSWORD=changeit

## Copy files into the image
# create and change into working directory
RUN mkdir ${APP_ROOT}}
WORKDIR ${APP_ROOT}}
# copying in file into current working directory
ADD main.js .
ADD package.json .
# copying in directory into current working directory, need to give the new directory name
ADD config config 
ADD public public 
ADD views views

## install dependencies
RUN npm install

## How an image is provision/run
# what port the container is exposing
EXPOSE ${APP_PORT}

## Add healthcheck to application
HEALTHCHECK --interval=60s --timeout=5s --retries=3 \
    CMD curl -f http://localhost:${APP_PORT}/health > /dev/null || exit 1

# entry point
ENTRYPOINT ["node", "main.js"]