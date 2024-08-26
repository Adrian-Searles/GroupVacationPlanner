FROM node:13.12.0-alpine as build

# set working directory
WORKDIR /frontend

# add `/app/node_modules/.bin` to $PATH
ENV PATH /frontend/node_modules/.bin:$PATH

# install app dependencies
COPY package.json ./
COPY package-lock.json ./
RUN npm install --silent
# RUN npm install react-scripts@3.4.1 -g --silent


# add app
COPY . ./
RUN npm run build

FROM nginx:alpine
# Copy built files from build stage to Nginx html directory
COPY --from=build /frontend/build /usr/share/nginx/html


EXPOSE 3000
EXPOSE 80



# Start Nginx
CMD ["nginx", "-g", "daemon off;"]



