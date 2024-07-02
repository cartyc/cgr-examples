# Build example Angular Application
FROM chainguard/node:latest as build

WORKDIR /app
COPY --chown=node:node package*.json /app/

RUN npm install

COPY --chown=node:node . /app

ARG configuration=production

RUN npm run build

## Runtime Stage
FROM chainguard/nginx
ENV PORT 8888
# Copy build artifacts from Build stage
COPY --from=build /app/dist /usr/share/nginx/html
