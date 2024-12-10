# Utiliser l'image officielle de PostgreSQL
FROM postgres:13

# Copier le fichier SQL pour initialiser la base de données
COPY words.sql /docker-entrypoint-initdb.d/

# Définir les variables d'environnement pour PostgreSQL
ENV POSTGRES_DB=wordsmith
ENV POSTGRES_USER=postgres
ENV POSTGRES_PASSWORD=postgres

# Définir le port d'écoute
EXPOSE 5432