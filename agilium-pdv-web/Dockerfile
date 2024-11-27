FROM node:19.5.0-alpine AS ng-build
RUN mkdir -p /app
WORKDIR /app
COPY package.json /app
RUN  npm install
COPY . /app
RUN $(npm bin)/ng build --prod

### Estagio 2
FROM nginx
COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=ng-build /app/dist/agilium-pdv-web /usr/share/nginx/html

EXPOSE 80