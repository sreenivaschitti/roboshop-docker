# FROM node:20
# RUN apk add --no-cache curl
# WORKDIR /app
# COPY package.json .
# COPY *.js .
# RUN npm install
# ENV MONGO="true"\
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node","server.js"]




FROM node:20-alpine AS builder
RUN apk add --no-cache curl

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .


FROM node:20.20.2-alpine3.23
WORKDIR /app
EXPOSE 8080
COPY --from=builder /app /app
ENV MONGO="true"\
    MONGO_URL="mongodb://mongodb:27017/catalogue"

#ENTRYPOINT ["server.js"]
CMD ["node","server.js"]

