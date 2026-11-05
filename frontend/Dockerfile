#Step 2: Download dependencies

FROM node:22-alpine AS builder

WORKDIR /app

COPY package*.json ./

RUN npm install


#Step 3: Run the code

COPY . .

RUN npm run build


#Serve with nginx

FROM nginx:1.27-alpine

COPY --from=builder /app/dist /usr/share/nginx/html


#Step 4: Expose to a port

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

