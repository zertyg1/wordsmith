# Utiliser l'image officielle de Go pour la compilation
FROM golang:1.17 as builder

# Définir le répertoire de travail
WORKDIR /app

# Copier le fichier source
COPY dispatcher.go .

# Compiler le programme
RUN go build -o dispatcher dispatcher.go

# Utiliser une image Ubuntu pour l'exécution
FROM ubuntu:20.04

# Installer les certificats nécessaires et curl
RUN apt-get update && apt-get install -y ca-certificates curl

# Copier l'exécutable compilé depuis l'étape de compilation
COPY --from=builder /app/dispatcher /dispatcher

# Copier le répertoire static
COPY static /static

# Définir le port d'écoute
EXPOSE 80

# Run the dispatcher
CMD ["./dispatcher"]