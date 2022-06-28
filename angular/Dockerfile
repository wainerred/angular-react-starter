#node
FROM node:alpine as builder
WORKDIR /usr/src/app
COPY package.json package-lock.json ./
RUN npm install
COPY . .
RUN npm run build -- --prod --output-path=/dist

#nginx
FROM nginx:alpine
RUN rm -rf /usr/share/nginx/html/*
EXPOSE 80
COPY --from=builder /dist /usr/share/nginx/html
COPY ./nginx.conf /etc/nginx/nginx.conf
ENTRYPOINT ["nginx"]
