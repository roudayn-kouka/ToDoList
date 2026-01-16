# === Étape 1 : build React ===
FROM node:18-alpine AS build

WORKDIR /usr/src/app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# === Étape 2 : serveur Nginx pour les fichiers statiques ===
FROM nginx:alpine

# Copier le build dans nginx
COPY --from=build /usr/src/app/build /usr/share/nginx/html

# Optionnel : config nginx custom (sinon conf par défaut)
# COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]