FROM node:25-alpine3.22 AS build

WORKDIR /app

COPY package.json .
RUN npm install

COPY server.js .

ENV INSTANA_AUTO_PROFILE true

FROM node:25-alpine3.22 AS runtime

RUN adduser -D appuser

WORKDIR /app

COPY --from=build /app /app

USER appuser

EXPOSE 8080

CMD ["node","server.js"]


