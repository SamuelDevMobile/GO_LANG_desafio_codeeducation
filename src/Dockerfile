FROM golang:1.16-alpine AS builder

WORKDIR /app

COPY go.mod .
RUN go mod download

COPY *.go ./

RUN go build -o /main

FROM scratch AS runner

WORKDIR /

COPY --from=builder /main /main

ENTRYPOINT ["/main"]
