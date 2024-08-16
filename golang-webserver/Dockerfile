FROM golang:1.22.6-bullseye AS builder
WORKDIR /app
COPY app.go .
RUN go mod init main && \
    CGO_ENABLED=0 go build

FROM scratch
EXPOSE 8080
COPY --from=builder /app/main /go/main
CMD ["/go/main"]


