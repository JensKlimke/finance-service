FROM node:17.3.0-alpine

# change to dir
WORKDIR /app

# copy
COPY . .

# install git
RUN apk update
RUN apk add git

# input parameters
ARG REACT_APP_API_URL

# checkout repo
RUN git clone -c advice.detachedHead=false --depth 1 --branch v1 https://github.com/JensKlimke/finance-app.git

# install and build
WORKDIR /app/finance-app
RUN npm ci
RUN npm i -g react-scripts serve
RUN npm run build

# expose port
EXPOSE 3001

# command
CMD [ "serve", "-l", "3001", "-s", "build" ]
