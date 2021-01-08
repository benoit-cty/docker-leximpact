FROM python:3.7
WORKDIR /opt
RUN apt update && apt upgrade -y && apt-get install -y libhdf5-dev && apt clean
# libhdf5-serial-dev 
RUN git clone https://github.com/leximpact/leximpact-server.git
WORKDIR /opt/leximpact-server
# TODO : Move missing dependencies numpy for "tables" in make install of leximpact
RUN pip install numpy
#
RUN make install
COPY env-leximpact-server.ini .env
#RUN make migrate
COPY entrypoint.sh .
RUN chmod a+x entrypoint.sh
EXPOSE 5000
ENTRYPOINT ["/opt/leximpact-server/entrypoint.sh"]