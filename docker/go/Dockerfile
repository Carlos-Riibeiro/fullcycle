FROM golang:1.15 as builder

WORKDIR /app

RUN go mod init example/hello
RUN go mod download

COPY main.go .
RUN GOOS=linux go build ./main.go

FROM scratch
WORKDIR /app
COPY --from=builder /app/main .

CMD ["/app/main"]