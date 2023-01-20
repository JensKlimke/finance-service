FROM node:17.3.0-alpine

WORKDIR /app

# install git
RUN apk update
RUN apk add git

# input parameters
ARG tag
ARG token

# checkout repo
RUN git clone -c advice.detachedHead=false --depth 1 --branch ${tag} https://${token}@github.com/JensKlimke/finance-db.git ./

# install
RUN npm ci

# expose port
EXPOSE 3000

# command
CMD ["npm", "start"]
