FROM node:12-alpine
WORKDIR /opt
# TODO : use a multistage build
RUN apk update && apk upgrade && \
    apk add --no-cache bash git openssh
RUN git clone https://github.com/leximpact/leximpact-client.git
WORKDIR /opt/leximpact-client
COPY env-leximpact-client.ini .env
RUN npm update
RUN npm install

#RUN npm run build
# Accept request from others than localhost :
RUN sed -i "s/server.listen(port);/server.listen(process.env.PORT, process.env.HOST);/" /opt/leximpact-client/server.js
EXPOSE 9001
CMD ["npm", "run", "dev"]