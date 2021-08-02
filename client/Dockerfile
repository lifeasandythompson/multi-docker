# Step 1: Use an existing docker image as a base
FROM node:alpine
WORKDIR '/app'

# Step 2: Install dependancies
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf 
COPY --from=0 /app/build /usr/share/nginx/html