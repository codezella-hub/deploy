# Étape 1 : Builder Angular
FROM node:18 AS builder

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build --configuration=production

# Étape 2 : Serve via Nginx
FROM nginx:alpine

# ⚠️ On copie le contenu du dossier "browser", pas "demo-ui"
COPY --from=builder /app/dist/demo-ui/browser /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
