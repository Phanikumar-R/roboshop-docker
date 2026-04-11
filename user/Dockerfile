FROM node:20
# This creates /app and move there
WORKDIR /app
# code is copied to /app
COPY package.json .
COPY *.js .
# installing dependencies
RUN npm install

# setup environment
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"\
    REDIS_URL="redis://redis:6379"
# execute the application
CMD ["node", "server.js"]


