#Below block is for multi stage build, where we are building the application in one stage and then copying the necessary files to another stage which will be used to run the application. This helps in reducing the size of the final image as we are not copying the node_modules folder which is not needed to run the application.
FROM node:20.20.2-alpine3.23 AS builder

WORKDIR /app
# code is copied to /app
COPY package.json .
COPY *.js .
# installing dependencies
RUN npm install



FROM node:20.20.2-alpine3.23

WORKDIR /app
# code is copied to /app

EXPOSE 8080

COPY --from=builder /app/ /app/


ENV MONGO="true" \
MONGO_URL="mongodb://mongodb:27017/catalogue"
# # execute the application
CMD ["node", "server.js"]


# Below block for building alpine image which is very small in size and has all the necessary dependencies to run node application
# FROM node:20.20.2-alpine3.23

# WORKDIR /app
# # code is copied to /app
# COPY package.json .
# COPY *.js .
# # installing dependencies
# RUN npm install

# # setup environment
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# # execute the application
# CMD ["node", "server.js"]






#Below block is for building the application using node image which is larger in size as it contains all the necessary dependencies to run node application, but it will take more time to build and run the application as compared to alpine image which is smaller in size and has all the necessary dependencies to run node application.
# FROM node:20
# # This creates /app and move there
# WORKDIR /app
# # code is copied to /app
# COPY package.json .
# COPY *.js .
# # installing dependencies
# RUN npm install

# # setup environment
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# # execute the application
# CMD ["node", "server.js"]


