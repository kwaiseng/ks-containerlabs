FROM node:latest

ENV	DB_HOST=nw-database	DB_Port=3306\
	DB_USER=root		DB_PASSWORD=changeit \
	APP_PORT=3000		APP_DIR=/app

WORKDIR ${APP_DIR}

# Next few lines add the local file to the container, using the same file name

ADD main.js .
ADD package.json .

# Next few lines add the local driectory  to the container,"." cant be used here. A name must be specified 
ADD config config
ADD public public
ADD views views

##  Following is specific to node

RUN npm install

## NExt, how to run

EXPOSE ${APP_PORT}

# this is running inside the container
HEALTHCHECK --interval=60s --timeout=5s --start-period=5s --retries=3 \
# To run the command; i.e. curl get /health , if fail exit with 1
	CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1

ENTRYPOINT ["node","main.js"] 
