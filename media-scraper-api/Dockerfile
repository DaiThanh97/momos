FROM node:14-alpine AS build

RUN mkdir /media-scraper-api
WORKDIR /media-scraper-api

COPY package*.json ./ 

RUN npm install

COPY . .
RUN npm run build

#---------------------------

FROM node:14-alpine

RUN mkdir /media-scraper-api
WORKDIR /media-scraper-api

COPY package.json ./

RUN npm install --only=production

COPY . .

COPY --from=build /media-scraper-api/dist ./dist

ENV NODE_ENV=production

CMD [ "npm", "run", "start:prod" ]
