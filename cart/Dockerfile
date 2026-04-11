FROM node:20
# This creates /app and move there
WORKDIR /app
# code is copied to /app
COPY package.json .
COPY *.js .
# installing dependencies
RUN npm install

# setup environment
ENV REDIS_HOST="redis" \
    CATALOGUE_HOST="catalogue"\
    CATALOGUE_PORT="8080" 
# execute the application
CMD ["node", "server.js"]


