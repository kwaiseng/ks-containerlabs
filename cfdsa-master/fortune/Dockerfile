# First, how to build the app
FROM node:latest

#these are environment paramaters
ENV APP_PORT=3000 APP_DIR=/fortune

# Create App_DIR 
WORKDIR ${APP_DIR}

#Copy files to AppDir
ADD main.js .
ADD package.json .
#directories must have a target name
ADD public public
ADD views views

RUN npm install 
## once this run, build is complete


# Next, how to run the image
EXPOSE	${APP_PORT}  


# this is running inside the container
HEALTHCHECK --interval=60s --timeout=5s --start-period=5s --retries=3 \
# To run the command; i.e. curl get /health , if fail exit with 1
	CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1
#
ENTRYPOINT ["node","main.js"]
#CMD
# optional command to run 
CMD [""]

