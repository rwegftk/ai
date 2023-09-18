FROM golang:alpine AS builder
WORKDIR /app
COPY . .
RUN go build -ldflags="-s -w" -tags netgo -trimpath -o go-proxy-bingai main.go
USER 10014

FROM alpine
WORKDIR /app
COPY --from=builder /app/go-proxy-bingai .


USER 10014   

EXPOSE 3000
CMD ["/app/go-proxy-bingai"]
