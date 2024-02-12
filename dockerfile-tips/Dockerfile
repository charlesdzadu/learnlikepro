FROM alpine:latest

# Les dépendances de votre application


# ❌ Ne pas faire
RUN apt-get update
RUN apt-get install -y package1

# ✅ Faire
RUN apt-get update && \
    apt-get install -y package1


# Étape de construction
FROM node:14 as builder
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build

# Étape de déploiement
FROM node:14-alpine
WORKDIR /app
COPY --from=builder /app/dist ./dist
CMD ["npm", "start"]


# ❌ Ne pas faire
RUN pip install -r requirements.txt
COPY . .

# ✅ Faire
RUN pip install -r requirements.txt
COPY app.py .


# Installation de dépendance (Moins fréquent)
COPY package.json .
RUN npm install

# Copie du code source (Plus fréquent)
COPY app/ .

