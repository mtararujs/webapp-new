FROM node:22 as build-stage

WORKDIR /frontend-app
COPY package.json ./
RUN npm install
COPY public public
COPY src src
RUN npm run build

FROM nginx:alpine
COPY --from=build-stage /frontend-app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]


# First stage:
#  node:22 used as base image
# All required code is copied (package.json, frontend application code)
# Commands “npm install” and “npm run build” are executed, so that there is react build available
# Next stage:
# E.g. nginx:alpine image is used as base
# Artifacts from first stage is copied (build, so explore where it could be found) to nginx target location (see documentation)
# Expose command defined to specify port which needs to be exposed (80)
# nginx command executed to start nginx service
