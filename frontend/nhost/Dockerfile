ARG VERSION

# FROM node:16-bullseye AS build
# WORKDIR /app
# COPY package.json ./
# COPY yarn.lock ./
# ADD tools tools
# RUN yarn install
# ADD . .
# RUN yarn nx build-server-assets console-ce


FROM hasura/graphql-engine:${VERSION}
RUN rm -rf /srv/console-assets
# COPY --from=build /app/dist/apps/server-assets-console-ce /srv/console-assets
ADD ./dist/apps/server-assets-console-ce /srv/console-assets
