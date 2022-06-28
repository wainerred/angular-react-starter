#node
FROM node:alpine as builder
WORKDIR /app
COPY package.json package-lock.json ./
ENV CI=1
RUN npm ci
COPY . .
RUN npm run build -- --prod --output-path=/dist
<<<<<<< HEAD
<<<<<<< HEAD
=======
>>>>>>> 32d2eaab0337a60ef15e874890771bb0db4e526e


#nginx
FROM nginx:alpine
RUN rm -rf /usr/share/nginx/html/*
COPY --from=builder /dist /usr/share/nginx/html
COPY ./nginx.conf /etc/nginx/nginx.conf
ENTRYPOINT ["nginx", "-g", "daemon off;"]
>>>>>>> parent of 13edf7f (правки докерфайла и nginx)
=======
>>>>>>> 32d2eaab0337a60ef15e874890771bb0db4e526e
