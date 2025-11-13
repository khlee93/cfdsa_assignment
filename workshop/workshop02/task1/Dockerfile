FROM node:20-alpine AS angular_builder

WORKDIR /src

COPY package.json package-lock.json ./
RUN npm install -g @angular/cli

COPY *.json .
COPY public public
COPY src src

RUN npm ci && ng build

FROM caddy:2.10

WORKDIR /app

COPY caddy/Caddyfile .

RUN mkdir -p html
COPY caddy/error.html html

COPY --from=angular_builder /src/dist/angular/browser/ html

ENV CADDY_PORT=3000

EXPOSE ${CADDY_PORT}

CMD ["caddy", "run", "--config", "/app/Caddyfile"]
