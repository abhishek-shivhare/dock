# base stage to have npm installed
FROM node:18-alpine AS base

# development stage
FROM base AS development 
ARG NODE_ENV=development 
ENV NODE_ENV=${NODE_ENV}
WORKDIR /usr/src/app 
COPY package.json ./ 
RUN npm install
COPY . . 
RUN npm run build

# production stage
FROM base AS production 
ARG NODE_ENV=production 
ENV NODE_ENV=${NODE_ENV} 
WORKDIR /usr/src/app 
COPY package.json ./ 
RUN npm install --prod
COPY --from=development /usr/src/app/dist ./dist 
 
# Add an env to save ARG
ENV APP_MAIN_FILE=dist/dock/main 
CMD node ${APP_MAIN_FILE}