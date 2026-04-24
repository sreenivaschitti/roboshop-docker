# FROM node:20-alpine
# WORKDIR /app
# COPY package.json .
# COPY *.js .
# EXPOSE 8080
# RUN npm install
# ENV REDIS_HOST="redis"\
#     CATALOGUE_HOST="catalogue"\
#     CATALOGUE_PORT="8080"
#     #MONGO_URL="mongodb://mongodb:27017/users"
# CMD ["node","server.js"]


FROM node:20-alpine AS builder


WORKDIR /app

COPY package.json .
COPY *.js .
RUN npm install


# ---- Runtime Stage ----
FROM node:20-alpine
WORKDIR /app
EXPOSE 8080

COPY --from=builder /app /app
# this handle with config map
# ENV REDIS_HOST="redis"\
#     CATALOGUE_HOST="catalogue"\
#     CATALOGUE_PORT="8080"

RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
RUN chown -R roboshop:roboshop /app
USER roboshop    
CMD ["node", "server.js"]