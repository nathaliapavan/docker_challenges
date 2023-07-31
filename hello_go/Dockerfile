# Estágio de compilação
FROM golang:1.20 AS builder

WORKDIR /app

# Copia o código fonte para o contêiner
COPY go.mod main.go ./

# Compila o código Go em um binário estático
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o app .

# Estágio de imagem final
FROM scratch

# Copia o binário estático do estágio de compilação para a imagem final
COPY --from=builder /app/app /app

# Executa o aplicativo Go
CMD ["/app"]
