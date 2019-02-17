FROM node:alpine as builder
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build
# RUN  cd dist && ls
# RUN ls /app/dist/frontend

# /app/dist contains required code

FROM nginx
EXPOSE 3000
# COPY --from=builder /app/nginx/nginx.conf /etc/nginx/nginx.conf
# COPY --from=builder /app/dist/frontend /usr/share/nginx/html

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html