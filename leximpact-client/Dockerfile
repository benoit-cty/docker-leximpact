FROM node:12-alpine
WORKDIR /opt
# TODO : use a multistage build
RUN apk update && apk upgrade && \
    apk add --no-cache bash git openssh
RUN git clone https://github.com/leximpact/leximpact-client.git
WORKDIR /opt/leximpact-client
COPY env-leximpact-client.ini .env
# Force version of Next.js to remove InvalidCharacterError bug in 9.5.5
RUN sed -i "s/\^9.3.5/9.3.5/" /opt/leximpact-client/package.json
RUN npm update
RUN npm install

#RUN npm run build
# Accept request from others than localhost :
RUN sed -i "s/server.listen(port);/server.listen(process.env.PORT, process.env.HOST);/" /opt/leximpact-client/server.js

EXPOSE 9001
CMD ["npm", "run", "dev"]