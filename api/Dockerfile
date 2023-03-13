FROM golang:alpine AS builder 

RUN mkdir /build

ADD . /build/ 

WORKDIR /build

RUN go build -o main .

#prod stage
FROM alpine:latest

RUN adduser -S -D -H -h /app appuser

COPY . /app

COPY --from=builder /build/main /app/

WORKDIR /app

EXPOSE 3000

CMD ["./main"]

