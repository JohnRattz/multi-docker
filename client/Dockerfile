FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY ./ ./
RUN npm run build # This will create a 'build' directory in WORKDIR.

# Run
FROM nginx
# This makes AWS Elastic Beanstalk expose the specified port.
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html