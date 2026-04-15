FROM node:20-alpine
WORKDIR /app
COPY package.json .
COPY *.js .
RUN npm install
ENV REDIS_HOST="redis"\
    CATALOGUE_HOST="catalogue"\
    CATALOGUE_PORT="8080"
    #MONGO_URL="mongodb://mongodb:27017/users"
CMD ["node","server.js"]