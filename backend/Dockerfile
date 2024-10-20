# FROM node:20.18.0-alpine3.20
# EXPOSE 8080
# ENV DB_HOST="mysql"
# RUN mkdir /opt/server
# WORKDIR /opt/server
# COPY package.json .
# COPY *.js .
# RUN npm install
# CMD ["node", "index.js"]

# Stage 1: Build Stage
FROM node:20 AS build
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN npm install

# Stage 2: Production Stage
FROM node:20.18.0-alpine3.20
WORKDIR /opt/server
COPY --from=build /opt/server /opt/server

EXPOSE 8080
ENV DB_HOST="mysql"
CMD ["node", "index.js"]
