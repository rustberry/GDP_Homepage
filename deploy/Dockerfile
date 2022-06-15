FROM docker.io/library/node:lts-alpine as webpage
COPY . /src
WORKDIR /src
RUN npm run build
COPY /src/dist /output

FROM docker.io/library/caddy:2
COPY deploy/Caddyfile /etc/caddy/Caddyfile
COPY --from webpage /output /app

EXPOSE 80

ENTRYPOINT ["caddy", "run", "--config", "/etc/caddy/Caddyfile", "--adapter", "caddyfile"]
