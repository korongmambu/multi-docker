FROM node:12-alpine as builder
USER node
RUN mkdir /home/node/app/
WORKDIR /home/node/app/
COPY ./package.json ./
RUN npm install
COPY ./ ./
CMD ["npm", "run", "build"]

FROM nginx:stable
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /home/node/app/ /usr/share/nginx/html/
