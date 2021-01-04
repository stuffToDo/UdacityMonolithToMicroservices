# Define the base image
FROM beevelop/ionic AS build

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies by copying
# package.json and package-lock.json
COPY package*.json ./
COPY ionic.config.json ./

# Install dependencies
RUN npm ci

# Copy app source
COPY . .

RUN ionic build

## Run 
FROM nginx:alpine
COPY --from=build /usr/src/app/www /usr/share/nginx/htm
