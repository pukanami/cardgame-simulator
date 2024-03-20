FROM nginx:latest

WORKDIR /app

RUN apt update \
&& apt upgrade \
&& apt install nodejs npm -y 

WORKDIR /app/cardgame-simulator

RUN npm i -g npm@10.5.0 \
&& npm i
