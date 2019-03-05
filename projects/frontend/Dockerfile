# PRODUCTION, with multi-step process
# STEP 1 (Build react app) Build Phase
FROM node:alpine as builder
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

# STEP 2 (Run NGINX) Run Phase
FROM nginx
COPY --from=builder /app/build /usr/share/nginx/html
