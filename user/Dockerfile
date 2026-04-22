# FROM node:20-alpine
# WORKDIR /app
# COPY package.json .
# COPY *.js .
# RUN npm install
# ENV MONGO="true"\
#     MONGO_URL="mongodb://mongodb:27017/catalogue"\
#     REDIS_URL='redis://redis:6379'
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
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"

RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
RUN chown -R roboshop:roboshop /app
USER roboshop    
CMD ["server.js"]
ENTRYPOINT ["node"]