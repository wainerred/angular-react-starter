#node
#FROM node:alpine as builder
#WORKDIR /app
#COPY package.json package-lock.json ./
#ENV CI=1
#RUN npm ci
#COPY . .
#RUN npm run build -- --prod --output-path=/dist

#nginx
#FROM nginx:alpine
#RUN rm -rf /usr/share/nginx/html/*
#COPY --from=builder /dist /usr/share/nginx/html
#COPY ./nginx.conf /etc/nginx/nginx.conf
#ENTRYPOINT ["nginx", "-g", "daemon off;"]



#node
FROM node:alpine as builder
WORKDIR /usr/src/app
COPY package.json package-lock.json ./
RUN npm install
COPY . .
RUN npm run build

#nginx
FROM nginx:alpine
EXPOSE 80
COPY --from=build /usr/src/app/dist/sample-app /usr/share/nginx/html
COPY ./nginx.conf /etc/nginx/nginx.conf
ENTRYPOINT ["nginx"]
